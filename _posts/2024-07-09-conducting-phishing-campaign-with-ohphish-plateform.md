---
layout: post
title: Conducting Phishing campaign with OhPhish Plateform
date: 2024-07-09 21:13 +0000
categories:
tags:
- cybersecurity
- phishing
- user awareness
---
Hello guys, it's been a while here.
I had the opportunity to conduct some phishing campaigns in the past with an awesome plateform that i want to share with : It's called **OhPhish**

## What to know about OhPhish ?
**Ohphish** is a cyber security platform, owned by EC Council, that works to improve the awareness of the users and promote good practices in relation to email security and other internet use by the staff. 

 It offers comprehensive tools for simulating phishing attacks, training employees, and assessing their vulnerability to phishing attempts. Some key features about Ohphish include:

 - *Phishing Simulation*: OhPhish provides various types of phishing simulations, including email phishing, SMS phishing (SMiShing), and voice phishing (vishing). These simulations help organizations assess their employees' susceptibility to different kinds of phishing attacks and provide immediate feedback and training to those who fall for the simulated attacks​

 - *Learning Management System (LMS)*: The platform includes an LMS that offers comprehensive security awareness training. The LMS features interactive training materials, such as videos, quizzes, and games, to engage employees and reinforce learning. It also allows organizations to track employees' progress and assign training modules based on their performance in simulations​ (EC-Council)​.

 - *Detailed Reporting*: OhPhish provides in-depth reports that help organizations understand their employees' risk levels and identify areas that need improvement. Reports include metrics such as user susceptibility ratings, the number of users tested, and detailed campaign statistics

 - *Customizable Training*: Organizations can customize the training content to match their specific needs and import their own training materials into the LMS. This flexibility ensures that the training is relevant and comprehensive

 - *Automated Training Assignments*: Employees who fail phishing simulations are automatically directed to relevant training materials. This just-in-time training approach ensures that employees receive immediate feedback and can learn from their mistakes in a timely manner.

## Ohphish Vs Gophish

Yeah i know you are used to using Gophish (even myslef before discovering Ohphish) but it requires more resources in real phishing engagement: I mean buying VPS and domain name. However, Ohphish makes life easier by saving you from buying all those stuffs. All you need is just whitelisting a specific IP adress at your client's mail server side.
Let's see clear about that in the following section.

## Setup Ohphish

Step1: Create an account on [https://aware.eccouncil.org/](https://aware.eccouncil.org/)

Click on *Get started* and fill in the form to have an account.
![Home page of Aware](/assets/img/Ohphish/form.png)
Be sure your email adress is a company email adress. For instance Gmail adresses will not work.

After filling in the form, you will get credentials to login into your account

![Mail received](/assets/img/Ohphish/mail-received.png)

So after login, the dashboard looks like as below

![OhPhish dashboard](/assets/img/Ohphish/dashboard.png)

Step2: Add your target user

At this step, we need to add users who will be our target. To add them, we need some pieces of information but the required are: name and email.

So from the dashboard, Go to *User Management*  menu then on *Users*. From there, you can add single user or bulk import from CSV file. The bulk import will be useful since in real scenario, you will have a bunch of users as target.

NB: The CSV file should be filled in based on the template given on the plateform.

You can also create a group of users based on your 

Step 3: Create the compaign

Here we are going to configure all neccessary to make our campaign ready

- Click on *Home* menu and then on *Email compaign*

![create campaign](/assets/img/Ohphish/create-campaign.png)

- Fill the form accordingly

![Filling the form](/assets/img/Ohphish/Filling-form.png)

My screenshot doesn't contain all the field to fill but basically, you need to fill 
    - Campaign Name : the name of your campaign
    - Campaign Type : Email
    -Type : Entice to click
      
    the second option (credentials capturing) won't be usable since we are using free trial version
    -Email Template: choose Existing template then
Somes fields are automatically filled when you choose your template and you're able to define users concerned by this campaign 






