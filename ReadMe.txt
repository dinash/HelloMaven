Running Jenkins docker image and sharing the local tomcat folder with the container:

docker run -d -v jenkins_home:/var/jenkins_home -v /home/ubuntu/tomcat/apache-tomcat-9.0.0.M10:/apache-tomcat-
9.0.0.M10 -p 8081:8080 -p 50000:50000 --restart=on-failure jenkins/jenkins:latest

Here first -v of jenkins_home is the volume that is shared with the container and host machine to maintain data between container stop and start

Second -v where the tomcat server's root path is share and mounted as "/apache-tomcat-9.0.0.M10" with the container.

In this way, when the build is successful within the jenkins container's job, we can copy the artifact to tomcat webapp folder to get it deployed.
