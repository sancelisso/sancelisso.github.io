---
layout: post
title: AD Persistence through SID History
date: 2024-02-07 15:48 +0000
---
Hello guys. I have learnt a new technic about persistence when you get Domain admin level right in Active Directory set and have the pleasure to write it down here.

## What is Persistence ?
A Persistence is a method that consist of regaining or maintaining access to a compromised machine or system without having to exploit the initial compromise steps all over again.

So in our context, we suppose we got access to the domain admin by chaining a lot of steps. It will be a little bit boring to take again all those step if you unfortunately lost your session.

Fortunately, there is a bunch of technic to maintain your accces in this case but this article will just cover that one concerning SID History
## What is SID ?

The SID (Security IDentifier) is a unique ID number that a computer or domain controller uses to identify you. It is a string of alphanumeric characters assigned to each user on a Windows computer, or to each user, group, and computer on a domain-controlled network

Exemple of SID:    `S-1-5-32-1045337234-12924708993-5683276719-19000`

Microsoft usually breaks this down into this pattern:

  `(SID)-(revision level)-(identifier-authority)-(subauthority1)-(subauthority2)-(etc)`

You can read more about it at [https://kb.iu.edu/d/aotl](https://kb.iu.edu/d/aotl)

## What is SID History ?

SID history is an Active Directory attribute that maintains a history of previous SID values if an object is moved from another domain. SIDs are prefixed with a unique domain identifier.

In fact, when a user in Domain A is migrated to Domain B, a new user account is created in DomainB and DomainA user’s SID is added to DomainB’s user account’s SID History attribute. This ensures that DomainB user can still access resources in DomainA.

SID history retains the old SIDs, allowing them to be used for access checks.

I would like to highlight that **Historical SIDs cannot be used to add users to new groups or roles, but can modify users or add them to a role or group only through the current object SID as defined by the domain.**

![SID History explained](/assets/img/AD-Persistence-SIDHistory/SIDHistory-explained!.jpg)
*SID History explained*

Now, enough history, let’s see how to perform this kind of persistence as an attacker
Now, enough history, let’s see how to perform this kind of persistence as an attacker

## SID History Injection

To achieve our goal, we need to use the tool called Mimikatz.

Mimikatz enables SID History injection to any user account (requires Domain Admin or equivalent rights).

In this scenario, the attacker creates the user account “bobafett” and adds the default administrator account for the domain, “ADSAdministrator” (RID 500), to the account’s SID History attribute.

```powershell
.\mimikatz "privilege::debug" "misc::addsid bobafett ADSAdministrator
```

![SIDHistory-injection.png](/assets/img/AD-Persistence-SIDHistory/SIDHistory-injection.png)

When the bobafett account logs on, all of the SIDs associated with the account are added to the user’s token which is used to determine access to resources. The SIDs associated with the account is the user’s SID, the group SIDs in which the user is a member (including groups that those groups are a member of), and SIDs contained in SID History.

Using the PowerShell Active Directory cmdlet “Get-ADUser”, we can see there is no group membership assigned to the bobafett account, though it does have a SID in SIDHistory (the ADSAdministrator account).

```powershell
get-aduser bobafett -properties sidhistory,memberof
```

![User-info.png](/assets/img/AD-Persistence-SIDHistory/User-info.png)

When bobafett logs on, the SIDs associated with the account are evaluated and access determined based on these SIDs. Since the bobafett account is associated with the ADSAdmnistrator account (RID 500), the bobafett account has all access the ADSAdministrator account has, including Domain Admin rights.

That’s all for the technic.

## Detection

For blue teaming perspective, the best way to detect this kind of exploitation is to enumerate all users with data in the SID History attribute and flag the ones which include SIDs in the same domain*.

If users haven’t been migrated, you can simply search for all users with data in the SIDHistory attribute. This is why it’s important to clean up SID History after a migration is complete (and the user is added to the correct groups for required resource access).

The PowerShell AD Cmdlet "Get-ADUser" is most useful for detecting "Same Domain SID History":

```powershell
Import-Module ActiveDirectory
[string]$DomainSID = ( (Get-ADDomain).DomainSID.Value )

Get-ADUser -Filter "SIDHistory -Like '*''” -Properties SIDHistory | `
Where { $_.SIDHistory -Like "$DomainSID-*" }
```

***Note**: In multi-domain forests, it is recommended to look for admin group SIDs (and member account SIDs) in every domain in the forest as well as trusted domains/forests.***

You can also look for events that have the following code:

- **4765** : SID History was added to an account.
- **4766** : An attempt to add SID History to an account failed.

## Funny Fact
It is funny but it is real. If you never knew about this kind of exploitation it you could not detect it.

![Joke-aboutSIDHistory.png](/assets/img/AD-Persistence-SIDHistory/Joke-about-detecting-SIDHistory.png)
*Funny fact*

## Useful links

- [https://adsecurity.org/?p=1772](https://adsecurity.org/?p=1772)
- [https://infohub.delltechnologies.com/l/powerscale-onefs-authentication-identity-management-and-authorization/sid-history-2/#:~:text=OneFS 8.0.,with a unique domain identifier](https://infohub.delltechnologies.com/l/powerscale-onefs-authentication-identity-management-and-authorization/sid-history-2/#:~:text=OneFS%208.0.,with%20a%20unique%20domain%20identifier).
- [https://student.labranet.jamk.fi/~AB7464/kotisivut/wr/ADPersistence.pdf](https://student.labranet.jamk.fi/~AB7464/kotisivut/wr/ADPersistence.pdf)
