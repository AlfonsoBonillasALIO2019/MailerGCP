---
templateKey: blog-post
title: Comparing AWS and GCP, Project 1
date: 2020-01-26T20:30:10.000Z
description: Comparing AWS and GCP, Project 1 - Send Mail Service
---

## Project 1: Send Mail Service


I was wondering if anybody else in the world had functionally compared AWS and GCP other than the default go to Gartner reviews and other review primarily coming from the source originator ( AWS, GCP ). I found a few blogs but decided that maybe its better to just practically build sample services and check out pros and cons during the process of building and afterwards measuring or try to measure performance given the tools provided by both AWS and GCP for its respective services.
The first easy and logical step for me was to build a mailing service using serverless architecture since I had already in-built one for our contact forms ( React JS based web app ) using AWS lambda and SES. From what I gathered from building that a couple of years ago now was how “easy” it was to build a lambda function but then it took some time ( not too long ) to figure out how to configure some things such as throttling and creating the endpoints so that they may be exposed to the outside world in AWS. Honestly once that was learned I did not have to re-learn because it is a really well structured way to set up these services in question. This is the basic set up:

![APIGatewayBasicSetup](/img/AWSAPISendMailBasic.jpg)

Now a few days ago I got certified by Google as Associate Cloud Engineer, which is really exciting to get and could only get after years of “poking” around with AWS, Azure services ( we built our first cloud app on Azure in 2012 ). Many of the concepts are similar to be honest except when dove into Kubernetes and pods which is a very particular way of managing applications and services that I have not built anything yet…hopefully Project N in a near future … 
For GCP I wanted to find something similar to AWS serverless Lambda and the first choice is Cloud Functions, so dove into building a Cloud Function that would do practically the same as the function in AWS to send emails. The go to tool for building this was Firebase, Firebase is actually a very complete tool for building and maintaining cloud functions and other services linked to Google such as Cloud Storage. The first step was to set up Firebase locally and link it ( log in ) to my existing account and create my first project there ( named Mailer for simplicity ). 
A little note prior, I looked for the most similar tool possible to API Gateway for Google and found APIGEE. APIGEE , I went through a tutorial to set up a basic endpoint, so you can actually do some cool stuff similar to API Gateway where can you set throttling,  manage different environments and add on some predefined policies such as converting an XML response to JSON to your flows ( pre and post ) which could be very useful. However, this tool unless I am mistaken and need to do some more research is not intended for you to build a Cloud Function or endpoint. This is why I resorted back to Cloud Functions building with Firebase/Google. These are the main differences I found during this short process, building the service took me 15 mins…( AWS a little more but again learning curve ):

* The Firebase CLI does not support deploying functions written in Python. So I resorted to writing in Node.JS ( Javascript or Typescript are actually provided as options ). If you really love Python, don’t use Firebase CLI you can write Cloud Functions in Python ( https://codelabs.developers.google.com/codelabs/cloud-functions-python-http/index.html?index=..%2F..index#0 )
*	As I mentioned previously, I could not find a way to set up throttling and security policies or validations, it seems I have to use APIGEE along with Firebase/Google Cloud for this…will do some more looking to see if could do it without APIGEE?
*	Yes the process to build a serverless function in GCP was farely simple and straightforward and Firebase does have a very intuitive monitoring dashboard and you could also use Stackdriving for performance monitoring. 
*	Did not have to use SES since I use GMAIL. I understand that with Google the SES-like service is SendGrid ( also a third party), will have to take a look at that soon.

![GoogleCloudFnPostMan](/img/SendMailCloudFnPostman.jpg)

![FirebaseCloudFnLog](/img/FirebaseCloudFnSendMailLog.jpg)

*A note on this which would have to find out further is cost-wise which is a less expensive solution, both solutions I have read are not too different in this respect.

Stay tuned for our next blog series on Comparing AWS and GCP, Project 2: File Uploading Service. We want to see which is more performant and cheaper again in a serverless environment ( Cloud Function -> DataStore, API Gateway / Lambda -> S3)I hope to have resolved the APIGEE question regarding throttling, I really don’t want to use an additional service for a couple of things to work for GCP.

**All the best!**
