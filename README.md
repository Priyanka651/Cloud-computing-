##DESCRIPTION
This project aims to guide you through setting up a time server on Ubuntu, using JSON to communicate time data over an HTTP API. 

##DESIGN

 *STEP1: Install Node.js on Ubuntu
 To begin, you need to install Node.js, which will serve as the runtime for our server. You can install Node.js by running the following commands:
  sudo apt update
sudo apt install nodejs npm

*Step 2: Install java and set Java path in ubuntu

*STEP 3: study time server basics and json then set linux configuration by using HTTP JSON API server and run into ubuntu .

*STEP4:  You can modify the Modify HTTP JSON API server.

##IMPLEMENT

  * Install ubuntu

    
  ![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/images/Screenshot%202024-10-04%20094517.png?raw=true)
 * Install JDK on Ubuntu 
 sudo apt-get update && sudo apt-get upgrade

![Alt text]( https://github.com/Priyanka651/Cloud-computing-/blob/main/images/2.png?raw=true)

 
 * Install default JDK
   sudo apt-get install default-jdk

   ![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/images/2.png?raw=true)

    * Set up java path
   Go to Control Panel > System Security > System > Advanced system settings
   set java path by going edit and set environment variables.
   
   ![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/2.png?raw=true)
   
   
   ![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/4.png?raw=true)

   * Linux Configuration
 Update .profile using the given code

![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/5.png?raw=true)

Then run profile.
.~/.profile
* Update .bashrc using the given code
* Run .bashrc
![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/6.png?raw=true)
  # Prepare Input Data
*For node.js version 10.x
$ curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -

*Install Node.js and npm
 sudo apt install nodejs
 sudo apt-get install -y nodejs

Verify that the Node.js and npm were successfully
$ node --version
$ npm --version

# Prepare code
. Build time_server.js file 
. create code 

![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/Screenshot%202024-10-07%20193513.png?raw=true)

#Run time_server.js in command prompt
node time_server.js 8000

 #Result
![alt text](https://github.com/Priyanka651/Cloud-computing-/blob/main/7.png?raw=true)
 



   
      
