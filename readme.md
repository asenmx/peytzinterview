# Technical assessment for Peytz &

# Co - IT Operations candidates

Dear Asen.
Thank you for taking the time to answer our technicalassessment as part of your
application at Peytz & Co.

This assessment is your opportunity to demonstrateyour technical skills within a
range of chosen subjects depending on the positionyou are applying for.

Don’t be alarmed if some of the questions are hardto answer. We have tried to
select a variety of questions that hold differentlevels of complexity. We do not
expect you to be able to answer all questions withinthe designated time-frame,
so you should decide which of the questions/answersbest demonstrate your
expertise.

We advise you to read through the entire assessmentbefore you start for you to
ensure that you have time to answer the questionsyou select.

Practical instructions 2

Assignment 1 : Ansible 2
Task 1.1: Nginx webserver 2
Task 1.2: Multiple vhosts 3
Task 1.3: nginx+php-fpm 3
Task 1.4: Usercreation 3
Task 1.5 Ansible test: 4
Task 1.6 Recap: 4

Assignment 2 : 5

Assignment 3 : DevOps pipelines 6

Assignment 4 : Docker containers 7

Assignment 5 : Microservices architecture 8

Assignment 6 : Amazon Web Services 9


## Practical instructions

You are allowed to use 90 minutesexactly, and itis up to you to keep this
deadline. The test starts at 07 .JULY at 08 : 00 CETand your answers must be
sent/shared no later than 07 .JULY at 09 : 30 CET

The questions require you to upload code or to answerin writing. Your answers
must be sent to us
A. as a PDF attachment in an email tojer@peytz.dkandhml@peytz.dk, or
B. by sharing a Google Docs document withjer@peytz.dkandhml@peytz.dk.

Your code can be placed in a GIT repository with alink in the PDF or Google Doc
document. If you place code in a private repo on github,please share the code
withjer@peyt.dk. The code must be committed and pushedwithin the deadline
as well.

Your code can also be attached to the mail.
Enjoy!

## Assignment 1 : Ansible

This part of the test will demonstrate your levelof knowledge about ansible. For
the purpose of this test, we have provisioned an Ubuntu20.04 server (in AWS).
Your ssh key (if you sent it to us beforehand) isadded to the user **_ubuntu_** that has
sudo rights on the machine. The machine is a newlyinstalled Ubuntu 20.04 LTS
server with no additional packages. It is open forall IP addresses on port 80 and
port 22. The machine will be deleted after the test

Start by ensuring that you can reach the machine byssh. The machine has IP


SSH access is required for you to complete the tasksin this assignment.
You are free to use the information from the Internet,Stack Overflow or other
tutorials, but please provide references to your sourcein the answer if you do so.

### Task 1.1: Nginx webserver

In the first task, we want you to provision the machineas an nginx webserver. The
webserver should answer requests on the IP addressabove, and serve a basic
HTML file of your choosing. So in short, the webpagemust be accessible from a
web browser.


Feel free to add additional packages besides nginx if you have a selection of
packages you like.

You must install everything with ansible, and in thewritten answer please explain
how you did this, and if possible include screenshotsof the ansible output.

You must include the ansible configuration you created,preferably as a GIT
repository.

### Task 1.2: Multiple vhosts

Building upon the previous task, you need to configurenginx to serve two
different virtual hosts. One should be a default virtualhost,possibly the one from
task 1.1. The other should answer on test.peytzaws.dk

As the domain does not resolve, you have to insertthe IP address in your
hostsfiles, or just validate that it works using curl.Please state how you verified it.

The content of the web page served by the v-hostsdoes not matter, but has to be
different.

### Task 1.3: nginx+php-fpm

Building on the task 1.1 or 1.2, you should configurethe server to use php-fpm to
server php files. You need to install and configurephp-fpm (with ansible) and
configure nginx to serve the php files.

The following php file must be able to run when accessingthe public IP address
of the server.

<?php
phpinfo();

As an answer, upload your ansible manifest includinga short explanation of how
you solved the task.

Feel free to “harden” or optimize php-fpm and nginxfor production, but default
settings are also ok for this task.

### Task 1.4: Usercreation

Create two users, with these settings:

```
● User Alpha should be added to the group's adm, andsudo.
● User Bravo should only be added to www-data.
```

Both users should use "sh" as the default shell, and both users should have a
group with the same name as the user. Try and use the least number of tasks you
can.

### Task 1.5 Ansible test:

Make a task that writes the epoch time in a file,but only if the current epoch time
ends with a 1,5 or 9.

Pingtest:
It is possible to “ping” “test.peytz.dk, test if itworks.
Make it possible for the machine to ping “test.peytz.dk”by only writing “ping test”.
If possible, do not edit the “/etc/hosts” file.
No matter if you got it working or not, explain yourthoughts on this task.

### Task 1.6 Recap:

Run all of your created playbook again.
Does the “PLAY RECAP” show any changes or failures?
Explain why it did or did not have any changes orfailures.

####Answer: **Recap shows only one change. The change is coming from restarting the nginx server, it would be good to have a handler instead, but no time to implement that.**


## Assignment 2 :

This assignment requires a written answer only, nocode. We ask for your
view/opinion regarding a specific problem. As-suchthere are no right or wrong
answers, we only ask for your opinion.

The answer can be short, but must include your opinionon the question. Feel free
to make a series of assumptions in your answer, butplease state them clearly.

_Problem_
We host a long range of websites and some of theseuse ElasticSearch in an older
version. The version has passed end-of-life and thenew version has functions that
are not backwards compatible. Consequently, it willnot be a trivial task to migrate
to the new ElasticSearch for the developers at Peytz& Co who use the old ES
version for customer solutions.

What is your opinion regarding the continued hostingof the old version of
ElasticSearch.
Please elaborate: Can we safely host the cluster ofES that is end-of-life, or would it
be better to force all solutions to migrate to thenew cluster, including spending
significant time fixing errors related to the migration?

####Answer: **I don't think it's a good idea to host versions that are end of life for security reasons. When a version is end of life it means, no patches are being done, no security updates, nothing. If new security vulnerability is found, we might get hacked. However, usually databases are heavily guarded with no direct access to them. This means sometimes it's okay to keep the old version for some time in order to fix the code.** 


## Assignment 3 : DevOps pipelines

A significant part of the daily task is to build pipelines.This applies for our
applications where pipelines are used for runningautomated tests, for building
containers, and often also for deployments.

We work with a number of different pipeline-toolssuch as Gitlab Runner, Azure
DevOps, and AWS Cloudbuild.

If you have experience working with some of thesetools or maybe from another
pipeline-tool, please provide (attach) a configuration(or screenshot) from a
pipeline including a written summary explaining whatthe purpose of this specific
pipeline is and why you created it the way you did.


## Assignment 4 : Docker containers

Some of the projects we work on at Peytc & Co. usecontainers for the operation of
the applications.

Below is an example of a Docker-file building a containerfor a GoLang-based
apiserver.

Briefly explain to us what Dockerfile does

FROM golang:1.15-alpine as _builder_
RUN apk add gcc=9.3.0-r2 git=2.26.2-r
COPY ./ /workdir
WORKDIR /workdir

ARG _GIT_REVISION_
RUN CGO_ENABLED= 0 GOOS=linux go install -tags netgo ./...

FROM alpine
RUN apk add ca-certificates
LABEL vendor="Peytz & Co A/S"
LABEL author="Jan-Erik Revsbech"
RUN addgroup -g 1001 - S appuser && adduser --uid= 1001 - S -s
/sbin/nologin -G appuser appuser

COPY --from= _builder_ /go/bin/apiserver.
COPY ./config ./config/
USER appuser
CMD ["./apiserver"]

####Answer: **Multi stage build docker file. First step is getting the golang image, copy the golang source code and install it. Second step is to copy apiserver bin  from the first step, copy some  config files and run it. **

## Assignment 5 : Microservices architecture

Some of the projects we run are built on a microservicesarchitecture, and
primarily as containers in some kind of orchestrationtool, Kubernetes or
cloud-service

Task 5. 1
Explain in your own words what to pay special attentionto, when working with
and operating projects built on microservices architecture.Feel free to include
topics like observability, tracing, routing, queueingsystems, etc.

####Answer: **Pay attention to state (if services are stateless or stateful), networking between the microservices is important part as well. It's really important to have the right connectivity and  security(what can see what) between microservices.
Task 5. 2
Many microservices architecture projects require accessto one or more queueing
systems.

In this task, one of our developers has contactedyou because the application she
is developing utilises AWS SQS for queueing.
The application she works on is an online transactionalsystem, and she has
observed that the events to the application don’talways appear to come in the
same sequence and even worse, sometimes the eventscome twice.

Her question to you is, can this behaviour reallybe correct, and is there something
wrong with the queueing system?
What is your answer to her? ( _a brief answer is ok_ )

####Answer: **There is standard queue and FIFO queues, standard ones can introduce duplicates, but FIFO queues are designed to never introduce duplicate messages. However, your message producer might introduce duplicates in certain scenarios: for example, if the producer sends a message, does not receive a response, and then resends the same message. Amazon SQS APIs provide deduplication functionality that prevents your message producer from sending duplicates. Any duplicates introduced by the message producer are removed within a 5-minute deduplication interval. Yes. FIFO (first-in-first-out) queues preserve the exact order in which messages are sent and received. If you use a FIFO queue, you don't have to place sequencing information in your messages. Standard queues provide a loose-FIFO capability that attempts to preserve the order of messages. However, because standard queues are designed to be massively scalable using a highly distributed architecture, receiving messages in the exact order they are sent is not guaranteed.**


## Assignment 6 : Amazon Web Services

Task 6. 1 Container orchestration architecture
We are building a new web api for a client, and wantto host the application on
AWS. The code is a containerized PHP application (Symfony),that also requires
some persistent storage.

The code is versioned in Github, and we would liketo have both a Production and
a Stage environment and implement a Continuous integrationpipeline that
automatically deploys the code to Staging.

Explain one or more options on how you would suggestwe host this solution, and
how to build the CD pipeline.


####Answer: **We can use codecommit to trigger  codebuild to build the containers and store them in ECR and trigger codepipeline to actually deploy  the service on ECS. It is important to know how the state will be kept will it be in s3 bucket or database or somewhere else (locally). Depending on how the state is kept we can figure out the rest. For different environment we can just use tags.


