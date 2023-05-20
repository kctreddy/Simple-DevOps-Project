#  Install & configure Maven build tool on Jenkins
Maven is a code build tool which used to convert your code to an artifact. this is a widely used plugin to build in continuous integration


#### Prerequisites
1. Jenkins server
2. C:: Maven Also depends on java, so java should be pre-installed to work with maven. We can also install maven independently in another server. In order to reduce complexity, in our case we are installing maven in Jenkins server.

#### Install Maven on Jenkins
1. Download maven packages https://maven.apache.org/download.cgi onto Jenkins server. In this case, I am using /opt/maven as my installation directory
 - Link : https://maven.apache.org/download.cgi
    ```sh
     # Creating maven directory under /opt
     mkdir /opt/maven
     cd /opt/maven
     # downloading maven version 3.6.0
     wget http://mirrors.estointernet.in/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.tar.gz
     tar -xvzf apache-maven-3.6.1-bin.tar.gz
     ```
	
1. Setup M2_HOME and M2 paths in .bash_profile of the user and add these to the path variable
   ```sh
   vi ~/.bash_profile
   M2_HOME=/opt/maven/apache-maven-3.6.1
   M2=$M2_HOME/bin
   PATH=<Existing_PATH>:$M2_HOME:$M2
   ```
#### ----------------------------------------------------------------------------------------------------
#### C:: Install Maven on Jenkins
1. Download maven packages https://maven.apache.org/download.cgi onto Jenkins server. In this case, I am using /opt/maven as my installation directory
 - Link : https://maven.apache.org/download.cgi
    ```sh
     # followed the same commands as mentioned in the video
     cd /opt
     # downloading maven version 3.6.0
     wget paste_the_copied_link_from_website
     tar -xvzf file.tar.gz
     mvn --version # works only in this path, so in order to work this anywhere we need set up M2_HOME, M2 and JAVA_HOME paths in .bash_profile of the user and add these to the path variable.
   vi ~/.bash_profile
      M2_HOME=/opt/maven/apache-maven-3.6.1
      M2=$M2_HOME/bin
      JAVA_HOME==/usr/lib/jvm/java-11-openjdk-11.0.18.0.10-1.amzn2.0.1.x86_64
      PATH=<Existing_PATH>:$M2_HOME:$M2:$JAVA_HOME
     ```
#### ----------------------------------------------------------------------------------------------------
#### Checkpoint 
1. logoff and login to check maven version
  
    ```sh
    mvn --version
    ```
So far we have completed the installation of maven software to support maven plugin on the jenkins console. Let's jump onto Jenkins to complete the remaining steps. 

### Setup maven on Jenkins console
1. Install maven plugin without restart  
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `Maven Invoker`
  - `Manage Jenkins` > `Jenkins Plugins` > `available` > `Maven Integration`

2. Configure maven path
  - `Manage Jenkins` > `Global Tool Configuration` > `Maven`
  - C:: `Manage Jenkins` > `Global Tool Configuration` > `JDK`
## C:: Build a maven project. Jenkins takes advantage of your ** POM files ** and drastically reduces the configuration. 
### C::
 Maven Build project:
  1st downloads all the dependencies which is required to build the project.
  2nd runs few test cases.
  3rd it builds the code.
  4th In our case case we have modules Server and Webapp. Both of them are also successfull.
   OVERALL BUILD IS SUCCESSFULL  -->  Created a ### WAR File
  `WebApp` -->  `target` -->  `surefire` ==>=>  Test cases results are stored in this path.
  
  Build Life cycle is made up of phases like 
   1. 
  
