![](images/Netflix_Logo.jpg)

---
![](images/netflix-ui-dd-spanish.jpg)

^ Netflix is global internet TV service
available in over 190 countries
localized to over 20 languages

---
![](images/netflix-dvd.jpg)

---
Netflix streaming service started in 2007

---
started with a datacenter

^
we weren't good at building datacenters

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
- create an installable Java microservice
- install and bake a microservice
- define our AWS deployment
- create a deployment pipeline

---
![fit](images/pipeline.png)

---
- create an installable Java microservice
- *install and bake a microservice*
- *define our AWS deployment*
- *construct a deployment pipeline*

---
# A simple microservice

- Groovy
- Spring Boot

---
![fit](images/code-war.png)

---
![fit](images/gradle-logo.jpg)

---
![fit](images/gradle-war.png)

---
![fit left autoplay](movies/gradle-build.mov)

let's run a build

---
![fit right](images/build-output-1-tree.png)

*Gradle's Application Plugin*
gives us a runnable app

---
![fit](images/pipeline.png)

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
![fit left autoplay](movies/gradle-build-deb.mov)

let's build a *Debian* package

---
![fit right](images/build-output-2-tree.png)

*Nebula's* ospackage plugin
produces a *Debian* package

---
- *create an installable Java microservice*
- install and bake a microservice
- *define our AWS deployment*
- *construct a deployment pipeline*

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

^ -e environment
-b base ami image

---
![fit](images/deploy-time.png)

---
![fit](images/deploy-time-annotated.png)

---
- *create an installable Java microservice*
- *install and bake a microservice*
- define our AWS deployment
- *construct a deployment pipeline*

---
![fit](images/pipeline.png)

---
AWS - create instances

---
# minimal instance needs
- security groups
- launch configurations
- elastic load balancers
- Amazon Machine Image

---
auto-scaling groups

---
![fit](images/spinnaker.png)

---
# Spinnaker

- Cloud deployment & pipelines
- microservice architecture
- Java & Groovy Spring Boot microservices

![right fit](images/spinnaker.png)

---
![fit](images/spinnaker-app.png)

---
![fit](images/spinnaker-create-1.png)

---
![fit](images/spinnaker-create-2.png)

---
![fit](images/spinnaker-create-3.png)

---
- *create an installable Java microservice*
- *install and bake a microservice*
- *define our AWS deployment*
- construct a deployment pipeline

---
Continuous delivery

---
![fit](images/spinnaker-infrastructure.png)

---
![fit](images/spinnaker-ami.png)
### Spinnaker community AMI

---
![fit](images/spinnaker-terraform.png)

### Bastion, Jenkins & Spinnaker

---
![fit right](images/jenkins-job.png)

## Jenkins build job
- checkout from Github
- `./gradlew clean build buildDeb`
- publish debian package

---
![fit](images/spinnaker-pipeline-setup-1.png)

---
![fit](images/spinnaker-pipeline-setup-2.png)

---
![fit](images/spinnaker-pipeline-setup-3.png)

---
![fit](images/spinnaker-pipeline-setup-4.png)

---
![fit](images/spinnaker-pipeline.png)

---
![fit](images/pipeline.png)

---
![fit](images/pipeline-second-asg.png)

---
![fit](images/pipeline-second-asg-2.png)

---
What's next?

---
- Eureka *(service discovery)*
- Edda *(track cloud changes)*
- Chaos Monkey *(kill prod instances)*

---
# Questions?
### Mike McGarr
### _*[@SonOfGarr](http://twitter.com/SonOfGarr)*_
### _*[MikeMcGarr.com](http://www.mikemcgarr.com)*_
