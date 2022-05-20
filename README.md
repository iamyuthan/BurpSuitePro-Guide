# Burp Suite Professional - Guide

> This guide will help you to understand the purpose and usage of the Burp Suite.

## Introduction
Burp Suite is a proxy tool which helps to view and interact with the communication between a client and the server. 
Still, didn't make sense? No worries, I will explain it from a lay man perspective. Just scroll down!

### Purpose of Burp Suite
Imagine you want to see the organs of a human or a baby inside a womb.

<img src="https://user-images.githubusercontent.com/83505381/169540851-deb2424f-0e7b-4bfc-b92f-fab3874d8f4a.png" width="200" height="300" /> <img src="https://user-images.githubusercontent.com/83505381/169540990-26284d67-7b64-4fc0-a132-c92f6a507eeb.png" width="200" height="300" />

How would you see? Do we need a surgery to know the condition or status of an organ or a baby?
Yes, you thought the right way. We do a scan or X-ray.

<img src="https://user-images.githubusercontent.com/83505381/169543825-0a3e3975-88f2-43b7-8cac-5fc35f21b199.png" width="300" height="200" /> <img src="https://user-images.githubusercontent.com/83505381/169543537-60e0c873-f5c8-4619-b958-699756467566.png" width="200" height="200" />

**Similarly, to understand or interact with the communication between a browser/client and a server/an application, we will need a proxy tool to achieve it.
So, the result we achieve through the proxy tool Burp Suite will be as shown below.**

![image](https://user-images.githubusercontent.com/83505381/169544806-a335541d-0894-4270-9c8b-370df4c3edb9.png)

**In this guide, we shall go through the different aspects of the tool and how to use them.**

# Burp Suite: Dashboard
## Dashboard Introduction

![image](https://user-images.githubusercontent.com/83505381/169546419-6ccfe76c-f256-4d8d-afa0-992c0fd2af6f.png)

Burp suite has many useful features in store for us, even right after starting up. As a user of the community version of burp, your options here will be somewhat limited, but still useful in debugging our project. We will start with one of the few free options available to us.

## Event log
This will display any event occurring in burp suite while we run it, this can range from errors to information to things we print out with our custom written extensions.
If you ever have issues intercepting traffic or decoding it, this is the first place i 
would look.

## Scans
We can differentiate between 3 different types of scans here, all 3 have their unique properties which we will go over in detail.

### Scan details
#### Scan types – Crawl
Crawling a website allows burp to automatically look for any URL or link it finds on the webpage that you give it and then attempt to surf there, and it will repeat the same actions. This can take one or multiple URLs as a starting point and go from there. I would like to point out that this does not serve the purpose of auditing those found items. 
The depth of this crawling and any other options can be set in the 'Scan configurations' which we will go over in the next section.

#### Scan types – Crawl and audit
We can also audit the crawled items directly, which will analyse the results and do things like static or dynamic code analysis (based on our settings in the Scan configurations).

#### Scan types – Audit selected items
This option is only available if we select several URLs from the sitemap and right click them. 

![image](https://user-images.githubusercontent.com/83505381/169551514-bdce131d-71f2-4071-8e5e-b0543560b6bf.png)
![image](https://user-images.githubusercontent.com/83505381/169551547-24131396-43d8-4233-abd4-9a6593df8ca8.png)

#### Protocol settings
Here we can define whether we want to test for both HTTPS and HTTP, or if we would like to define which protocols to test for.

### Scan configurations

![image](https://user-images.githubusercontent.com/83505381/169552609-c3f62df6-67a4-4a60-a9f5-f52111240059.png)

In here we define rules for our scan. Every line in here can consist of one or several rules and can be combined. For example, we can choose to do all the audits except for the JavaScript analysis, and also we might want to limit or crawling to 30 minutes max. This can easily be done by adding some built-in rules. 

![image](https://user-images.githubusercontent.com/83505381/169553319-b89ca76a-cd5a-437f-b0a5-e0109ba4101b.png)

But we can also build our own rules here by pressing the “New ...” button. This will give us a choice between crawling and auditing. If you set audit rules on a crawler only jobs, that's of course not going to have any effect.

![image](https://user-images.githubusercontent.com/83505381/169553612-4d2fb73d-c00c-42ca-bf3c-f50be8788998.png)

It really pays off to name your rules properly if you ever want to reuse them. This is a confusing part, and having ambiguous names for rule sets can be perplexing.
Next we intend to set up the different options we have. If we would like to enable a rule, we need to click open the respective section and the rule will automatically be enabled if it is filled in.

![image](https://user-images.githubusercontent.com/83505381/169553719-10d4533b-a7b9-4d59-ac7a-0ca4763cc2cc.png)

Most of these settings speak for themselves, but we will be going over each one of them in a separate section, so we don't have to interrupt the flow of the course. 
We can also save our rules in the library, this will enable us to reuse them later on. 

### Application login
Occasionally, when crawling, burp will encounter a login screen. If we have credentials available, we can enter them here, allowing for an authenticated crawling. This will expose a lot more functionality to us but is not foolproof as burp sometimes doesn't recognise the login pages; however, it is still much better than never being able to crawl a website authenticated.

![image](https://user-images.githubusercontent.com/83505381/169554675-4128a6b0-b90a-4601-aa1a-fba1362f9b91.png)

You can give a label to the credentials, which are just to make it easier to recognise which credentials you have in front of you.

### Resource pool
This allows us to create “resource pools” which are merely variables to which we assign a certain value of maximum concurrent requests, delay between those requests and other options. 
We can then use specific resource pools for specific jobs.

![image](https://user-images.githubusercontent.com/83505381/169554984-9abc2950-9c5e-463d-b065-e026f04ef01d.png)

## Live task
Live scanning can perform the same auditing actions as the crawling and auditing can do, but this will happen on all the requests you are executing or that are coming in while you are manually exploring the website.

## Issue activity + Advisory
When scanning, burp will come across some issues. Whenever it does, it will display them here. 
Everything here pretty much speaks for itself, and burp will explain things in the “Advisory” section when we click on an issue in the “Issue activity” window.

![image](https://user-images.githubusercontent.com/83505381/169555308-8fafcc11-c2ab-4607-b322-f4d861299a2e.png)

The most useful part here are the filters, they allow us to show specific vulnerability types, making it easier to distinguish between the ones we care about and the ones we do not. I've found that almost none of the issues in here are worth it to investigate when I am doing pentesting.
