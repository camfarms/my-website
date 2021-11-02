+++
title = "casePlace"
author = "Cameron Farmer"
date = "2021-10-17T13:31:50-04:00"
workingDirectory = "~/root/content/myPortfolio/schoolWork/casePlace.md"
weight = 1 
draft = false
toc = true
description = "CasePlace is a web-based application that my team and I created for our Senior project. We built this application using React, and spent an entire semester designing, planning, developing, and polishing it. Check out CasePlace in its final form!"
+++

## Intro

Here is a [link](https://case-place-5t56t.ondigitalocean.app) to our website!

CasePlace is oriented towards prospective and current students of Case Western Reserve University (CWRU) as well as any parents or guests visiting the campus. Its purpose is to make our urban campus easier to navigate by offering an interactive GoogleMap interface with pre-loaded points of interest. 

CasePlace is a web application that 5 peers and myself worked together to create for our Senior Project. We built this application using React (so it even works on mobile) and it utilizes the GoogleMaps API to make an interactive map of our university's campus! It was inspired by an [existing web-page that CWRU has linked](https://webapps.case.edu/map/) on their home website that we thought was too clunky and cluttered for people who are new to the campus. 

We believe CasePlace is an improvement over this webpage due to the sorting functionality it offers. Newcomers to our campus are unlikely to know the names of buildings, or what they are even looking for. CasePlace simplifies this by allowing them to filter and sort the pinned locations into administrative buildings, restaurants, bus stops, etc. 

## Design

For the design phase, we spent a lot of time working on wireframes in order to make sure we knew exactly what we wanted before starting program. For the purposes of wireframing we used Figma, which is like the Google Docs of wireframing. Here is an example of our very early drafts!

{{< image src="/img/casePlace/earlyWireframe.png" >}}

Once we had decided on a general layout, we began to focus more on the style and feel of our application. We thought it would be fitting to make our website match [CWRU's professional websites](https://case.edu) for continuity purposes as these websites all share the same audience. In order to emulate CWRU's websites, we started by using their same color palette and fonts. We then moved on to making our CSS emulate features across CWRU's websites for buttons, modals, dropdowns, etc. Here is one of our later design drafts!

{{< image src="/img/casePlace/hiResWireframe.png" >}}

Using CWRU's map page as a model, we took our ideas from the design phase and got to work to make it happen. Here is a side by side comparison -- decide for yourself whether or not we matched CWRU's feel. 
 | CasePlace | CWRU's Page |
 |-------------|-----------|
 | {{< image src="/img/casePlace/casePlace.png" >}} | {{< image src="/img/casePlace/caseWebApp.png" >}} |

 ## Technology

 For this project we used a variety of different languages and applications. 

 - Framework: React (with CSS and HTML)
 - Version Control: Git
 - Ticketing System: Jira
 - Design Tool: Figma
 - Server Host: Digital Ocean

 Luckily for us, we were able to use Jira, Figma, and Digital Ocean for *FREE* due to all of us being students! 

 This was my first time using React and I really enjoyed using it. It strikes me as a (maybe a little *too*) robust, but powerful framework. I'm no expert, but I think you could make just about any web-app you want using React. 

 ## Group Organization

 Since this was a multi-month long project, it was super important to us as a group that we stayed on top of our work and made steady progress throughout the semester. In order to adhere to this, we elected one of our members, Elias, as project manager for the semester. Elias was the perfect candidate since he had just worked as a project management intern for Google the previous Summer! 

 We started the semester by planning out our sprints and setting dates for certain deadlines. For instance, we allotted 1 week for setting up our environments, 3 weeks for design, and 2 weeks for debugging. We also all agreed to meet with one another twice a week to hold "scrum" meetings in which we would discuss the status of our project and what we were all working on. 

 Elias made is super easy for all us to keep track of our tasks due to his familiarity with Jira. For each sprint, he would make a new story and break it into sub-tasks to be distributed amongst us in the group. As a result of how organized we were, we ended up ahead of schedule by the end of the semester while many groups were cramming to get their projects working. 

 ## Personal Accomplishments

Fortunately, I worked with 5 amazing people and didn't have to deal with people not pulling their own weight. We were an extremely cohesive group who were all committed to working on this project as if it were a professional task for a client rather than a professor. 

I personally worked on almost all aspects of the project, but I am especially proud of what I managed to accomplish during the design phase. While using Figma, I had the realization that I really enjoyed the challenge of designing a page that was both intuitive AND aesthetic. This pushed me to take the lead on a number of things during the design phase, such as the CSS used for our components. 

During the development phase I worked on both the front-end and back-end. For instance, one of my subtasks was to implement the tooltips that open when a user clicks on one of the pins on our map. This required me to write logic for an action handler in JSX that would trigger a new HTML component to appear that I styled in CSS. 

{{< image src="/img/casePlace/tooltip.png" >}}

... You do not want to know how long I spent trying to get the tooltip to have that tiny little triangle at the top! 

## Lessons Learned

The success of our project was entirely due to our organization. From working on CasePlace I learned how valuable an agile development cycle can be, and how the structure it offers helps everyone on the team stay on task. Furthermore, without a good project manager and a clear division of labor (i.e. Jira) it would have been much, *much* more difficult for us to work together effectively. 