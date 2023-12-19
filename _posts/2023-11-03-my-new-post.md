---
layout: post
title: My OSCP Review (2023)
categories: [certification review]
tags: [OSCP, pentest, cybersecurity, certification]
date: 2023-11-03 10:30 +0000
---
I have been certified OSCP since a while and i have the pleasure to share with you my experience about this prestigious certification.

## OSCP, Kezako ?

OSCP, defined as OffSec Certified Professional is a one of famous cybersecurity certification delivered by OffSec organization which is about ethical hacking or penetration testing.
This certification is obtained by sitting for an proctored exam which occurs during 24 hours. The goal of the exam is to hack machines and earn enough point to pass.

If you are here, i bet you've already have idea about all of this. The main goal of this artcile is to share how i prepared myself to tackle the exam. It may motivate you to prepare yourself.

## How was i prepared ?
It took me approximately 5 months to prepared. I have the opportunity to study with some mates during this journey since it was very helpful to work and learn from them. My preparation curses are detailed as follow:
### One Month on TryHackme premium
I started my OSCP journey on this platform and did almost all rooms of the Offensive path but i didn't really take note of what i was doing 🙈 Don't do like me please :)

I remembered an hilarious things while doing rooms here. One of my colleague saw me performing SQL Injection by using SQLmap and exclaimed in this terms: <<What are you doing with SQLmap while preparing for the OSCP ? >>

I got immediatly afraid and took look at prohibited tools by Offsec and tried to avoid them while working.

### Three Months on HackTheBox (HTB)
The hardest part of my preparation was on HTB. I pwned around 80+ machines and took note of almost of them. The boxes pwned was from TJ NULL list and recommended by one of my elders.

The list of boxes done can be found here : [OSCP Prep Boxes-2023](../../assets/OSCP_Prep_Boxes-2023.xlsx)

While doing those boxes, i learn a lot of things. It helps me to sharpen my pentest methodology and when i got stuck, i could rely on write-ups from [0xdf](https://0xdf.gitlab.io/), [ippsec videos](https://ippsec.rocks) and [rizemon](https://rizemon.github.io/)

### Two Months and few weeks on OffSec material
After finishing my journey on HTB, i decided to buy the voucher and started learning the official course material offered by Offsec.

I read and took note of the importants things form the course. The course material was good for me, so i digested it as well. The topics covered in the course can be found [here](https://www.offsec.com/wp-content/uploads/2023/03/pen-200-pwk-syllabus.pdf)

I completed all the exercises of the courses and completed almost all the labs except the challenge 3 which is not similar to OSCP reality as said by the course.

By doing this, i secured the 10 bonus points since i don't know what i will face during the exam. I didn't want to loose any chance to pass 😃

While spending my time on this part, i could call for help from the OffSec discord, or from my study mates when i got stuck on exercises or labs

### Two weeks on Proving Ground platform
For this, i relied on TJ NULL list again but there are some boxes which are removed. So i did specially all boxes i could find relatives to Active Directory and then some standalones machines.

| Active Directory   | Standalones |
| -------------------| ----------- |
| Heist - Hucth - Vault - Resourced |  ClamAV -Fail- Banzai - Craft - Nibbles - Nickel|
|                                   |  Hunit - Astronaut- Dibble - Slort - Zino     |

I was proud to do this since it saves me a bunch of time during the exam 😃 I got similar attack vector, so copy-pasting commands was the fastest way 😆

## Time management

 Since i am working as Cybersecurity analyst, i managed to do my daily tasks and then focus on my training. In fact, i can spend approximately 6 or 8 hours per day on my training: It depends on availability. On the week-end, i enjoy myself by taking rest and entertaining  or continuing my training if weekly training goal was not achieved.

 Nearing the end of the training, it was so relax. I could get some days without pwning machines or anything else.

## Before sitting for the exam
Before sitting for the exam, i was sure to master well all topics of OffSec material and reviewed my notes about mock exams (OSCP-A, OSCP-B and OSCP-C challenges) and others interesting things. I also wrote down some checking to do when i will get stuck on the exam.

I even got some days of holiday in order to relax and fresh my mind. During those days, i take rest and read some writeups but no boxes pwning. I stayed away a little bit from my computer.

## The D-Day

My exam should start at 7pm on Wednesday but i got some technical issues and alerted Offsec support. The issue was fixed around 8pm.

I started by the Acitive Directory set. It was a little bit straight forward. Look closely at all your findings is the key.

I was taking taking note and screenshots as well as i am progressing

I successfully tackled my first standalone machine since it was like an easy machine.

So i was securing 60 points at this step and logically i got the necessary to pass since i was eligible to 10 points bonus but my goal is to earn the 70 points in my own since Offsec could mess up to attribute you the bonus point accordingly and send you fail mail later (story read from some OSCP review)

Now my next machine is easy like the previous but i got stuck in rabbit hole for few hours 😨. After some rest, i got other idea and was blind to go further. I took rest and took rest again and boom i follow like a baby all the step of my exploit and got the initial access. It just got paid trying harder process 😂😜

I was on cloud nine as ever. I would like to try pivoting to perform privilege escalation for the next but it fails. Since i achieved my goal, i gave up on that.

After that, i reviewed my notes, screenshots and flags submitted. I was about to forget to submit one flag, fortunately i noticed it after my review and took action.

The last machine was difficult for me. I could not got any entry point: a weird Windows machine ! 😌

I started writing the report but i felt uncomfortable with the presence of the proctor. So, i asked to end the exam. I ended my exam around 4 pm of the following day and took a rain check on report writeup because i was exhausted and had to go hospital for my remaining injections (Yeah i got sick few days before the exam 😢)

## Report writing
After coming back from hospital, i took rest and ate. Then i jumped on report writing. It was a little bit easy since i took note properly of my findings. The extra only things at this step is to suit my findings to known CWEs (Common Weakness Enumeration) and describe them normally. Report writing looks easy but it took me a bunch of time. I finished the following day (Friday) around 4 pm after fixing some formatting issues within the document.

After the submission, i went outside and ate my favorite meal to award myself of all of these efforts 😎

Waiting for the exam result is another hardest time. I was afraid, just thinking if i put all necessary information in my report. I was checking my mail box every time !

Finally, i got the confirmation that i passed on the Offsec platform and few minutes later i got the expected mail 🔥

## Useful links

- My favorite note taking app : [notion.so](https://www.notion.so/)
- My favorite screenshot taking app : [flameshot](https://flameshot.org/)
- TryHackme : [tryhackme.com](https://tryhackme.com/)
- HackTheBox : [https://www.hackthebox.com/](https://www.hackthebox.com/)
- Proving Ground : [https://www.offsec.com/labs/individual/](https://www.offsec.com/labs/individual/)
- OSCP course : [https://www.offsec.com/courses/pen-200/](https://www.offsec.com/courses/pen-200/)
- OSCP course syllabus : [https://www.offsec.com/wp-content/uploads/2023/03/pen-200-pwk-syllabus.pdf](https://www.offsec.com/wp-content/uploads/2023/03/pen-200-pwk-syllabus.pdf)
- OSCP Prep Boxes 2023 : [OSCP Prep Boxes-2023](../../assets/OSCP_Prep_Boxes-2023.xlsx)
