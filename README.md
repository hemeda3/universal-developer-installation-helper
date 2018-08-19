<pre>
 #####1-  add sudoers ( no copy paste in this steps, just type:) ########

sudo nano /etc/sudoers  # nano is light editor for terminal
developer   ALL = NOPASSWD: ALL  # developer is your username

press ctrl + o # save 
press enter button
press ctrl + x # close nano editor 
press enter button
sudo usermod -a -G sudo developer
sudo usermod -G vboxsf -a


####2- connect to share bok  #######

install guest CD tools
sudo adduser developer vboxsf

sudo apt-get install -y build-essential make gcc  linux-headers-$(uname -r) linux-headers-generic make linux-source  linux-generic linux-signed-generic

logout or restart
 
you should see new icon in your desktop looks like hardisk with name sf_new 
you should  be able to doubleclick on it and you should be able to see all files and folders inside it, which shared from Windows  **
####3- go to your shared folder in windows and import TD ssl  certificate (TDBankGroupSHA2InternalBrowsingRootCertificate.crt) you got from me by Email,  => AhmedYousri.SalamaMohammed@Td.com
####4- import ssl to firefox  ############
1- open firefox by click on your left side bar in ubuntu
2- in firefox press ctrl + t 
3- type or copy in url :                   about:preferences#privacy
4- scroll to end of the window , then click view certificates button 
5- select Authority tab 
6- press import 
7- Go to share folder in your desktop **
8- select your TD ssl with name :  TDBankGroupSHA2InternalBrowsingRootCertificate.crt and press OK/Import
9- will display  your options, select all and press OK
10- then you can access google

########## download chrome using firefox ###################
go to  https://www.google.com/chrome/ and follow screenshots (chromeXXXX .png)

REDUX https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=en

########## time sync + GIT installation ####################
open commandline and do 
################# time sync#################
sudo apt-get install ntp
################# install git #################
sudo apt-get install git
################# install curl #################
sudo apt-get install curl
################# install NVM to prepare for Nodejs =======
REFENRECE :::
https://www.digitalocean.com/community/tutorials/how-to-install-node-js-with-nvm-node-version-manager-on-a-vps

run :
curl -k https://raw.githubusercontent.com/creationix/nvm/v0.11.1/install.sh | bash
close + open new console 
run  in terminal :
source ~/.profile
nvm ls-remote
these command should show you LIST all Node Versions 
again run :
nvm install 8.11.3
nvm use 8.11.3
source ~/.profile

n=$(which node);n=${n%/bin/node}; chmod -R 755 $n/bin/*; sudo cp -r $n/{bin,lib,share} /usr/local

open new terminal 
run 
 npm -v
 node -v 
 #enjoy

############ succss vs code#################
1-https://go.microsoft.com/fwlink/?LinkID=760868
2- sudo dpkg -i 
=> *sudo dpkg -i code_1.26.0-1534177765_amd64.deb
=> verify it and open it => run in terminal =>      code .    

###################################################### FRONT END FINISH ###################################################################################################################################
#########################################################################################################################################################################################
============ install jdk 8==================
http://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html

jdk-8u172-linux-x64.tar.gz



select  jdk-8u172-linux-x64.tar.gz click + download

download in chrome jdk-8u172-linux-x64.tar.gz

RUN:::::

cd /home/"your_user_name"/Downloads  #cd /home/developer/Downloads

sudo mkdir -p /usr/local/java

sudo cp -r ~/Downloads/jdk-8u172-linux-x64.tar.gz /usr/local/java/

cd /usr/local/java

sudo tar xvzf jdk-8u172-linux-x64.tar.gz
# remove tow tar.gz for free space
ls #you should see jdk1.8.0_172

sudo nano /etc/profile

****Scroll down to the end of the file using your arrow keys and add the following lines below to the end of your /etc/profile file:****
#JDK 8
JAVA_HOME=/usr/local/java/jdk1.8.0_172

JRE_HOME=/usr/local/java/jdk1.8.0_172

PATH=$PATH:$JRE_HOME/bin:$JAVA_HOME/bin

export JAVA_HOME

export JRE_HOME

export PATH

#####
Then run these commands :::
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.8.0_172/bin/java" 1 && sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.8.0_172/bin/javac" 1 && sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.8.0_172/bin/javaws" 1 && sudo update-alternatives --set java /usr/local/java/jdk1.8.0_172/bin/java && sudo update-alternatives --set javac /usr/local/java/jdk1.8.0_172/bin/javac && sudo update-alternatives --set javaws /usr/local/java/jdk1.8.0_172/bin/javaws && source /etc/profile 
 sudo update-alternatives --config java # this optional if you have two JDK ex JDK8,JDK7, and you want to change to  specific version this will make it easy


java -version

You should receive a message which displays:


java version "1.8.0_172"
Java(TM) SE Runtime Environment (build 1.8.0_172-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.172-b11, mixed mode)

add java home 
sudo nano /etc/environment
add to the end of file this line( this line we got from java alternatives command)

JAVA_HOME="/usr/local/java/jdk1.8.0_172/bin/java"


=============================================
============install jdk 7====================


chrome go to :::::: => http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html

select  jdk-7u80-linux-x64.tar.gz click + download

download in chrome jdk-7u80-linux-x64.tar.gz

RUN:::::

cd /home/"your_user_name"/Downloads  #cd /home/developer/Downloads

sudo mkdir -p /usr/local/java

sudo cp -r jdk-7u80-linux-x64.tar.gz /usr/local/java/

cd /usr/local/java

sudo tar xvzf jdk-7u80-linux-x64.tar.gz

ls #you should see jdk1.7.0_80

sudo nano /etc/profile

****Scroll down to the end of the file using your arrow keys and add the following lines below to the end of your /etc/profile file:****

JAVA_HOME=/usr/local/java/jdk1.7.0_80

JRE_HOME=/usr/local/java/jdk1.7.0_80

PATH=$PATH:$JRE_HOME/bin:$JAVA_HOME/bin

export JAVA_HOME

export JRE_HOME

export PATH

########################################
Then run these commands :::
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.7.0_80/bin/java" 1

sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.7.0_80/bin/javac" 1

sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.7.0_80/bin/javaws" 1

sudo update-alternatives --set java /usr/local/java/jdk1.7.0_80/bin/java

sudo update-alternatives --set javac /usr/local/java/jdk1.7.0_80/bin/javac

sudo update-alternatives --set javaws /usr/local/java/jdk1.7.0_80/bin/javaws

source /etc/profile
sudo update-alternatives --config java # this optional if you have two JDK ex JDK8,JDK7, and you want to change to  specific version this will make it easy


java -version

You should receive a message which displays:

java version "1.7.0_80"

Java(TM) SE Runtime Environment (build 1.7.0_80-b15)

Java HotSpot(TM) 64-Bit Server VM (build 24.80-b11, mixed mode)
## refrence : https://askubuntu.com/questions/1034387/how-can-i-install-jdk7-on-ubuntu-18-04-lts-64bit

==============================================================================================================================================

######################################## INSTALL INTLIJI IDEA ######################################################################
 go to chrome and download 
 
https://www.jetbrains.com/idea/download/download-thanks.html?platform=linux&code=IIC
automatically will download ideaIC-2018.2.1.tar.gz # go to break
RUN ::::

sudo mkdir -p /opt/Idea && sudo  tar xf ~/Downloads/ideaIC-2018*.tar.gz -C /opt/Idea && sudo chmod +x /opt/Idea/idea*/bin/idea.sh && /opt/Idea/idea*/bin/idea.sh



run it + it automatically will suggest to create DesktopEntiry for you just press OK
######################################## INSTALL  JBOSS 6.4 EA ######################################################################
######################################## INSTALL  GIT SourceTree ######################################################################
######################################## INSTALL  GitFlow relase management ######################################################################
######################################## INSTALL  Maven ######################################################################
  mkdir /home/developer/.m2
  then copy settings.xml from your windows location 
  sudo nano /home/developer/.m2/settings.xml

  cd /opt/ && sudo wget http://www-eu.apache.org/dist/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
sudo tar -xvzf apache-maven-3.3.9-bin.tar.gz && sudo mv apache-maven-3.3.9 maven 
 
Step 4: Setup environment variables
Next, you will need to setup the environment variables such as M2_HOME, M2, MAVEN_OPTS, and PATH. You can do this by creating a mavenenv.sh file inside of the /etc/profile.d/ directory.

sudo nano ~/.profile
source ~/.profile

Add the following lines:

export M2_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}
Save and close the file, update its permissions, then load the environment variables with the following command:

Step 5: Verify installation in NEW TERMINAL 
Once everything has been successfully configured, check the version of the Apache Maven.

mvn --version

  
######################################## INSTALL  postman API  ######################################################################
######################################## INSTALL  Gradle ######################################################################
######################################## INSTALL  Scala ######################################################################
######################################## INSTALL  Gatling Scala Performance &LoadTesting ######################################################################

 ######################################## INSTALL  JHIPSER CLI ######################################################################
######################################## INSTALL  Keycloack ######################################################################
######################################## INSTALL  ELK stack (ElasticSearch Logstash/FileBeat Kibana) Centerlized ASync Logging ##########################################
######################################## INSTALL   GoLang ######################################################################
######################################## INSTALL   DartLang ######################################################################
######################################## INSTALL   MangoDB ######################################################################
######################################## INSTALL   CouchBase+Couchbase Async server###################################################




######################################## INSTALL  Docker ######################################################################
######################################## INSTALL  Docker-Compose ######################################################################
######################################## INSTALL  Private Docker Registery ######################################################################
######################################## INSTALL  Private NPM Registery ######################################################################
######################################## INSTALL  Private Nexus Register ######################################################################

######################################## INSTALL  Docker ######################################################################

######################################## INSTALL  Kubernates ######################################################################
######################################## INSTALL  Jenkins ######################################################################
######################################## INSTALL  Bamboo ######################################################################

######################################## INSTALL  OPENSHIFT ######################################################################
######################################## INSTALL  IBM Bluprint ######################################################################
######################################## INSTALL  Oracke Wricker ######################################################################
######################################## INSTALL  Oracke Wricker ######################################################################


######################################## INSTALL  NGINX ######################################################################
######################################## INSTALL  REACT ######################################################################
######################################## INSTALL  REACT Native - MObile ######################################################################
######################################## INSTALL  NativeScript - Mobile ######################################################################


================make .sh bash =======================
 
 
 
</pre>
