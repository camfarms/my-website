+++
title = "SAP"
author = "Cameron Farmer"
date = "2021-11-07T15:25:08-05:00"
workingDirectory = "~/root/workXp/softDevInternships/SAP.md"
weight = 1 
draft = false
toc = true
description = "During Summer 2020 and 2021 I had the opportunity to intern with SAP. I worked alongside a team of professional developers and made improvements to SAP's Learning Management Suite. Check out some of the stuff I learned!"
+++

## Intro

In April 2020 I accepted a summer internship with **SAP**. I had a wonderful time working with a team of extremely talented developers. The experience helped me grow as a professional and taught me many valuable technical skills! 

The following summer I was given a return offer to intern with the same team at SAP and I jumped at the opportunity. My second internship with SAP was just as rewarding and I was able to build off the things I had learned the previous year. 

## Meet the Team

I was part of the "K-Force" team working on SAP's Learning Management Suite (LMS) as an intern. Below is a picture of all of us at a company lunch from June 2021!

{{< figure src="/img/workXp/sapTeam.png" caption="(From left to right) Birla, Bhargavi, Krupali, Sarath, Shweta, Divya, Shiva, and Me" >}}

**Krupali** is the **team lead** for K-Force and she is AWESOME! Not only is she a talented developer, she is also an excellent communicator and it was an absolute pleasure to work under her leadership. 
**Sarath and Shiva** were my **mentors** who I was extremely thankful for. They are both kind and capable; they are also infinitely patient and were always willing to answer my questions when I inevitably got stuck. 
**Birla** is K-Force's **lead architect** making him responsible for code reviews. He has an incredibly deep understanding of SAP's enormous code base... and a great sense of humor. All of K-Force's pull requests had to go through him for review and he would check that the code changes followed the conventions and standards of SAP's code base. 

The team as a whole was extraordinary. Everyone was so friendly and talented; it was a pleasure to work with them. I am so thankful to all of K-Force for being so welcoming and helpful, I couldn't have asked for a better team!

## My Contributions

I made improvements to SAP's LMS that are now **live** on the most recent version of their software! But first, **what is LMS**? LMS is like a **professional version of BlackBoard or Canvas**; it is an all-in-one application for assigning, taking, and completing online learning courses such as certifications, on-boarding education, etc. 

One of my features displayed specific information for a given class, such as "*How to Avoid Phishing Attacks*". The implementation required that I **pass information** pertaining to the class to a database and **use it to query** for the relevant table information to be displayed. The query results then needed to be **converted into Java objects** before being passed back to the point of request to be displayed. This may seem like a relatively simple process -- use local variables to query a database and return the results, right?  
Well you would be correct if the SAP code base wasn't **hundreds of thousands of lines long**. To access the database, I needed to pass the information through both the **data and business layer of the application** -- a process that involved a number of existing and new Java objects. Here is the API diagram I made for my requirement to give you an idea of complexity of the code base I had to navigate:  

{{< image src="/img/workXp/api.png" >}}

The hardest part when implementing my features was simply **understanding** the existing code -- it was just so overwhelming at first! I spent hours parsing and tracing the codebase until I had an inkling of the existing mechanisms. Once my research was complete, I would propose a solution to Krupali and Birla, and with their go-ahead I would start implementation! I repeated this process numerous times throughout my internships which has given me a lot of confidence in my ability to understand complex code bases. 

## Lessons Learned

I learned so much from my time at SAP, but one of the most important lessons I took away from the experience was the importance of **asking for help**. When I first started, I was terribly nervous to ask anyone for help understanding the code base because I didn't want to look stupid. Looking back, that was silly and I wish it hadn't slowed me down as much as it did. 
Thankfully, I had amazing mentors who quickly made it clear to me that it was OK to be confused and ask questions. They were extremely sympathetic to my struggle and were always happy to explain parts of the code that I couldn't wrap my head around. This made me realize that being confused was just a part of the job which gave me a huge boost in confidence. I will no longer be worried about seeming foolish when asking questions -- sometimes, you just need some help.

