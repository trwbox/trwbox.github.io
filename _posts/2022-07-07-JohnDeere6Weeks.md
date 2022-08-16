---
title: "John Deere Internship at 6 Weeks"
excerpt: "Talking about my summer internship at John Deere at halfway through"
ride_along_gallery:
    - url: /assets/images/JohnDeere/combine.jpg
      image_path: /assets/images/JohnDeere/combine.jpg
      alt: "The front of a combine, with a tractor coming towards the photographer"
    - url: /assets/images/JohnDeere/sprayer-front.jpg
      image_path: /assets/images/JohnDeere/sprayer-front.jpg
      alt: "View facing out the front of the cab of a sprayer while driving down the road in transport mode"
    - url: /assets/images/JohnDeere/sprayer-side.jpg
      image_path: /assets/images/JohnDeere/sprayer-side.jpg
      alt: "View facing left of the cab of a sprayer while driving down the road in transport mode"
    - url: /assets/images/JohnDeere/inside-combine-1.jpg
      image_path: /assets/images/JohnDeere/inside-combine-1.jpg
      alt: "Picture from a combine cab facing down towards the harvest head"
    - url: /assets/images/JohnDeere/inside-combine-2.jpg
      image_path: /assets/images/JohnDeere/inside-combine-2.jpg
      alt: "Picture from a combine cab facing down towards the harvest head"
tags:
    - internship
categories:
    - posts
---
## Let's start off at the beginning ##

At the end of May, I started a new internship on the Cloud Security Team at John Deere. Since I am just over halfway through the internship, I thought I would write about how the internship is going.

This being my first internship, I was not sure what to expect going in, or what I was going to get out of it. From the minute I got my laptop that first day, I feel like I have been learning so much. At times it has been rather overwhelming, but everyday I'm feeling a little better about what is going on. Starting out that first week, I did a large amount of HR related teachings, and then moved onto training on Agile development.

### Time for some real training ###

Prior to this, I had never heard of, or experienced Agile development before. At first, it seemed like a lot of meetings, and instead of increasing the team's productivity, it would lower it. After a few weeks of all the meetings, I started to really like Agile Development. In Agile Development, your goal is to deliver a small piece of a project in a short time period, instead of delivering a whole project all at once. This breaking up of a large project into smaller chunks was very helpful with my understanding of the projects, and where in development they were. This also let me jump into the portions of the project that I knew how to help in, while listening and learning in the parts that I did not know. In the process, I also made an obsidian notebook that can be found [here](/agile-development-notebook) if you want to see how I thought through it.

After that first week with HR and Agile trainings, I started to get into the team specific training. Coming into the team, I did not have very much knowledge in cloud concepts or AWS. Thankfully, John Deere understands this, and offers subscriptions to [ACloudGuru](https://acloudguru.com) for all staff and reimbursements for any certificates earned. The first suggested certificate is the AWS Cloud Practitioner. I spent the next couple of weeks going through all the training videos and the labs for the course to prepare me for the Cloud Practitioner Exam. As I was going through this course, it was overwhelming with the number of services that AWS offered, but I felt like I was slowly getting the hang of it. This culminated in taking the AWS Certified Cloud Practitioner Exam and passing!

### Actual Work I have done ###

This led into actually getting some work done on my internship. The biggest and most memorable thing that I have done so far is working a project that involves EC2 port control. Being a member of the Cloud Security Team we are in control of what is and is not allowed on policies in John Deere's section of AWS. Currently EC2 instances public ports are required to be reviewed by a person before they are approved. With the only enforcement being an automated check that happens every so often, where the team gets a ticket to fix the issue. This means a person could change their instance to allow something like SSH when they are not approved for it and the only consequence is some nasty email until it is fixed. The goal of the project is to automate large portions of this procedure to approve ports, keep record of the approved ports, and add additional enforcement to prevent a user from doing something not allowed. Users will be able to request ports by modifying files on a file share, these changes will get processed to decide if they can be automatically approved, or not. Then they will then get sent through to a database to house what the approved ports for each security group are. The database is the part that I have worked on most. I was tasked with creating a DynamoDB that is going to be used as a cache that stores the currently authorized ports without having to make a call to pull a whole file from the file server every call. I have also had to create a lambda function for the database that will pull messages from a queue that is filled up automatically when the files in the file share are changed, and creating new entries when a new security group is created. This then all comes together with AWS Conformance Packs that will invoke a Lambda that will automatically change security groups that are not compliant with the ports that they have been approved.

### Some more fun things I've done ###

While the AWS Security work is the Cyber Security part of the internship. There are also a variety of activities that I get the opportunity to participate in that are not related to Cyber Security. So far I have gotten the chance to participate in an internship conference where we got to hear from various speakers including century farmers, team leaders, and senior management. They had some very inspiring talks about what we can accomplish in our internship, and how we can make the most out of our time at John Deere. The other most exciting thing that I have gotten to do is actually a couple of experiences. There have been a pair of opportunities where I have gotten to go out to John Deere test facilities, and get to know more about the vehicles John Deere makes. Not only did this include getting to be up close, and talking to people who know a lot about the specifics of the combines, tractors, and sprayers John Deere makes. But I got the chance to ride in them, and see them in action. While I grew up around some farm equipment with being in a small Iowa town, and having a grandpa that farmed, it was very interesting to see what the brand new technology could do.

{% include gallery id="ride_along_gallery" layout="half" caption="The pictures I took during the ride along event." %}

### Some plans for the next 6 weeks ###

While the final 6 weeks I will be doing more work with my team. There are a few things that I will be doing that are not part of that work. I will be creating a final intern project that will be presented at the end of the summer to employees of John Deere. It is about something that I have did, and learned about over the course of the summer, and needs to be different from the other interns on my team. Right now, I have a few ideas of what I might do, but nothing concrete, but with it being a month or so away, I'm not too worried about finding something. I also have plans to job shadow a member of the Vulnerability Management team, and getting to spend time talking the members of the brand new Red Team about what their day to day holds.
