# Docker-Deployment-manually
Create Docker Image: Got to project directory: eg: D:\eclipse\Docker-Practice\hello-docker> 
and run the below command.
Now use maven command mvn clean install dockerfile:build to create docker image.

[INFO] Image will be built as hello-howtodoinjava/hello-docker:latest
[INFO]
[INFO] Step 1/5 : FROM openjdk:8-jdk-alpine
[INFO] Pulling from library/openjdk
[INFO] Digest: sha256:2b1f15e04904dd44a2667a07e34c628ac4b239f92f413b587538f801a0a57c88
[INFO] Status: Image is up to date for openjdk:8-jdk-alpine
[INFO]  ---> 478bf389b75b
[INFO] Step 2/5 : VOLUME /tmp
[INFO]  ---> Using cache
[INFO]  ---> f4f6473b3c25
[INFO] Step 3/5 : ADD target/hello-docker-0.0.1-SNAPSHOT.jar hello-docker-app.jar
[INFO]  ---> ce7491518508
[INFO] Removing intermediate container c74867501651
[INFO] Step 4/5 : ENV JAVA_OPTS ""
[INFO]  ---> Running in f7cd27710bf3
[INFO]  ---> 086226135205
[INFO] Removing intermediate container f7cd27710bf3
[INFO] Step 5/5 : ENTRYPOINT sh -c java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /hello-docker-app.jar
[INFO]  ---> Running in 9ef14a442715
[INFO]  ---> bf14919a32e2
[INFO] Removing intermediate container 9ef14a442715
[INFO] Successfully built bf14919a32e2
[INFO] Successfully tagged hello-howtodoinjava/hello-docker:latest
[INFO]
[INFO] Detected build of image with id bf14919a32e2
[INFO] Building jar: F:\Study\Technical Writings\docker\hello-docker\target\hello-docker-0.0.1-SNAPSHOT-docker-info.jar
[INFO] Successfully built hello-howtodoinjava/hello-docker:latest
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------

Deploy and Run Docker Image
So we have created the Docker Image (i.e. hello-docker-0.0.1-SNAPSHOT-docker-info.jar). We also have a installed docker container running in our local machine.

Now, to run the docker image inside installed docker container, we will use below command.
docker run -p 8080:9080 -t hello-howtodoinjava/hello-docker  --name hello-docker-image

Here the option -p 8080:9080 is important. It says that expose port 8080 for internal port 9080. Remember our application is running in port 9080 inside docker image and we will access that in port 8080 from outside Docker container.

Now access the application with URL http://192.168.99.100:8080/hello/sajal. Notice that the browser output is same as output of standalone REST API on localhost.
