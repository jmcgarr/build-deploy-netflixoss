![](images/Netflix_Logo.jpg)

---
![](images/netflix-ui-dd-spanish.jpg)

---
![](images/netflix-dvd.jpg)

---
Netflix streaming service started in 2008

---
Oracle outage

---
Migrate to the cloud

---
![fit](images/aws.png)

^ - As we migrated to the cloud, we learned a lot of lessons

---
![300%](https://raw.githubusercontent.com/Netflix/netflix.github.com/master/images/Netflix-OSS-Logo.png)

^ - we learned a lot of lessons
- these lessons have been codified in our OSS
- we began open sourcing in _____

---
![](images/netflixoss-logos.png)

^ - 128 repos in Netflix org

---
# [fit] _Build_ and _deploy_ to the cloud using
![inline 300%](https://raw.githubusercontent.com/Netflix/netflix.github.com/master/images/Netflix-OSS-Logo.png)

### Mike McGarr <br> _*[@SonOfGarr](http://twitter.com/SonOfGarr)*_ <br> _*[MikeMcGarr.com](http://www.mikemcgarr.com)*_

^ I will start with an example

---
- create an *installable* Java microservice
- standup a Netflix OSS AWS *infrastructure*
- package and deploy to cloud

---
![fit](images/pipeline.png)

---
![fit](images/pipeline-step1.png)

---
# A simple microservice

- Java 8 (GROOVY?)
- Spring Boot

---
![fit](images/code-war.png)

---
![fit](images/gradle-logo.jpg)

---
![fit](images/gradle-war.png)

---
![fit left](images/build-output-1.png)

let's run a build

---
![fit right](images/build-output-1-tree.png)

*Gradle's Application Plugin*
gives us a runnable app

---
![fit](images/pipeline-step2.png)

^ - go back to our pipeline
- need to convert code to Debian

---
Immutable server pattern

^ - never change code running on an instance
- prevent configuration drift
- easily scale up and scale down

---
![fit](images/nebula-vertical.png)

^ should I remove this slide?

---
![fit left](images/nebula-website.png)

## Nebula Plugins

dependency lock *plugin*
resolution rules *plugin*
dependency recommender *plugin*
lint *plugin*
metrics *plugin*
test *plugin*
publishing *plugin*
ospackage *plugin*

---
![fit left](images/gradle-ospackage.png)

1. Add the *Nebula ospackage* plugin (blue)
2. Define the *Debian* package content (red)

---
![fit left](images/gradle-ospackage.png)

![fit](images/gradle-ospackage-zoom.png)

---
![fit left](images/build-output-2.png)

let's build a *Debian* package

---
![fit right](images/build-output-2-tree.png)

*Nebula's* ospackage plugin
produces a *Debian* package

---
![fit](images/pipeline-step3.png)

---
unit of deployment

---
# Baking

![fit inline](images/baking-process.png)

---
![fit](images/baseami-process.png)

---
![fit left](images/aminator.png)

Aminator

---
![fit](images/aminator-output.png)

---
`sudo aminate /
-e ec2_aptitude_linux /
-b ubuntu-base-ami-ebs /
helloworld_1.0.0_all.deb`

![fit](images/aminator-output.png)

---
![fit](images/pipeline-step4.png)

---
# AWS (to cover)
- Auto scaling group concept
- map an AMI to an ASG
- ASG's contain homogenous instances
- new deployments create new ASG's
- ASG's are essentially versioned
- How do you group ASG's to an application?

---
![fit](images/spinnaker.png)

---
What's missing
- commit to build to bake to deploy
-

---
# Deployment infrastructure

- GitHub
- Jenkins
- Spinnaker

---
Continuous delivery

---
