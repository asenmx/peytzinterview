Assignment 1: Ansible 2
Task 1.1: Nginx webserver 2 - done
Task 1.2: Multiple vhosts 3 - done 
Task 1.3: nginx+php-fpm 3 - done

Task 1.6: Recap shows only one change. The change is coming from restarting the nginx server, it would be good to have a handler instead, but no time to implement that.





**Assignment 2:**
I don't think it's a good idea to host versions that are end of life for security reasons. When a version is end of life it means, no patches are being done, no security updates, nothing. If new security vulnerability is found, we might get hacked. However, usually databases are heavily guarded with no direct access to them. This means sometimes it's okay to keep the old version for some time in order to fix the code. 


**Assignment 3:** not enough time for this one



**Assignment 4:** Multi stage build docker file. First step is getting the golang image, copy the golang source code and install it. Second step is to copy apiserver bin  from the first step, copy some  config files and run it.


**Assignment 5:** Pay attention to state (if services are stateless or stateful), networking between the microservices is important part as well. It's really important to have the right connectivity and  security(what can see what) between microservices.
**have no idea about task 5.2**


**Assignment 6:** We can use codecommit to trigger  codebuild to build the containers and store them in ECR and trigger codepipeline to actually deploy  the service on ECS. It is important to know how the state will be kept will it be in s3 bucket or database or somewhere else (locally). Depending on how the state is kept we can figure out the rest. For different environment we can just use tags.
