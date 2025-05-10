# Integration of an IDS(snort) with a SIEM solution(splunk) for real-time security monitoring

## Objective
To implement a real-time security monitoring system by integrating Snort IDS with Splunk Enterprise through a Universal Forwarder, enabling centralized log collection, custom alerting, and interactive dashboards for effective intrusion detection and analysis.This setup helps monitor network activity more easily and allows quick detection and response to potential threats.

### Skills Learned
- Splunk Enterprise Installation and Configuration – Setting up and managing a SIEM platform for data ingestion and analysis.

- Splunk Universal Forwarder Deployment – Installing and configuring forwarders for remote log collection.

- Log Forwarding and Centralized Log Management – Sending and managing logs from different sources to a central SIEM.

- Snort IDS Installation and Configuration – Deploying an open-source intrusion detection system on Linux.

- SIEM and IDS Integration – Connecting Snort with Splunk to monitor security events in real time.

- Alert Creation in Splunk – Setting up custom alerts based on specific security events or log patterns.

- Dashboard Design in Splunk – Building visual dashboards for better monitoring and threat visibility.

- Basic Linux Administration – Managing Ubuntu VMs, installing packages, and configuring services.

- Security Monitoring and Threat Detection Concepts – Understanding how to detect and analyze suspicious activities.

- Network Traffic Analysis – Capturing and interpreting logs from IDS tools for network security insights.
- SPL - Search Processing Language is Splunk's query language, used to search, analyze, and visualize machine data indexed in Splunk
 
 ### Tools Used

- Splunk Enterprise – For centralized log management, analysis, dashboards, and alerting (installed on Windows).

- Splunk Universal Forwarder – Lightweight log forwarder to send logs from Ubuntu VM to Splunk Enterprise.

- Snort IDS – Open-source Intrusion Detection System for monitoring and generating network security alerts.

- Ubuntu (Linux VM) – Host operating system for Snort and Splunk Universal Forwarder setup.

- Windows OS – Platform for hosting Splunk Enterprise server.

- kali linux - used this operating system as attacking machine to test the setup.

- VirtualBox  – For running the Ubuntu virtual machine and attacking machine (kali linux).

- Command Line Tools (Linux CLI) – For configuration, log viewing, and managing services in Ubuntu and to test the setup.

- Web Browser (e.g., Chrome, Firefox) – To access and manage the Splunk web interface.
  

  ### Project map
  

  ![integration fo an IDS with a SIEM solution for intrusion monitoring](https://github.com/user-attachments/assets/845a92fe-868d-40ea-9806-c6f100cb131d)

  ### STEPS

  I’ll be installing and configuring Splunk’s universal forwarder, Snort in the ubuntu virtual machine as well as a Splunk enterpriser server in windows from scratch in the following steps.

  ## NOTE: The actual integration of Snort with the real-time monitoring SIEM solution begins at Step 11. Up to Step 10, we will focus on building the real-time monitoring SIEM solution
  
  ### Step 1
  ## Downloading and Installing splunk enterpriser

  To download the splunk enterpriser go to their official page and under products you will see free Trails and Downloads as following image below

  ![image](https://github.com/user-attachments/assets/38c552d9-aeb9-46b9-bc83-2dbcc5254297)

  When you click on that Free Trails and Downloads , there will be splunk enterpriser as shown in below

  ![image](https://github.com/user-attachments/assets/bd21a7b3-5552-46f2-9207-e724abebd529)

  when you click on get my free trail it will ask you to sign up , so proceed with that

  ![image](https://github.com/user-attachments/assets/dba83595-d193-414c-b1b1-5b6168eea2ea)

  login with your credentials and click on the download now

  ![image](https://github.com/user-attachments/assets/37225414-1d3d-47b0-ab73-524c5f64d1af)

## Install splunk enterpriser

Double click on the downloaded msi file , choose customize Options tab

![image](https://github.com/user-attachments/assets/577b0f27-bff0-466c-9718-8e77dad28bb6)

click on next and choose Local system in next step then give your own credentials 

![image](https://github.com/user-attachments/assets/75493975-10ba-4e9d-acdc-9c073d2439f0)

click on install,it will start installing and it will take some time to complete installation 

![image](https://github.com/user-attachments/assets/24e5aaa6-b127-4608-928f-e06c0d6c37c6)

### step 2
open the splunk enterpriser by using search tab in taskbar 

![image](https://github.com/user-attachments/assets/5b82c6e4-8679-49e7-81c2-7886b3000f9d)

login with your credentials (those given while installing splunk ) and it's interface will be like as below 

![image](https://github.com/user-attachments/assets/e7cf0be8-38e4-4284-b54c-3ca1659df1d0)

### step 3
### configure the forwarding and receiving
click on the settings , under DATA there will be Forwarding and Receiving, choose that option 

![image](https://github.com/user-attachments/assets/d64719e9-a22f-4ae8-8ef9-842173dc702b)

click on the "+Add new" at the Receive data 

![image](https://github.com/user-attachments/assets/8ed0fad2-1be2-4976-a886-22372cdf2f2a)

i will go with default port which is 9997 in my case

![image](https://github.com/user-attachments/assets/64dd28c8-83a4-4d3a-a3d4-4c17f2cd40c0)

 we had done with adding receiving port

 ![image](https://github.com/user-attachments/assets/b8c38c80-c5dd-419e-92e3-15558e209fdc)

### step 4
## Creating new index 
click on the settings tab and choose indexes under DATA

![image](https://github.com/user-attachments/assets/0a3560df-cdb0-452e-8984-48404144a8af)

click on New Index 
![image](https://github.com/user-attachments/assets/eba36327-9d18-4dcd-804d-1cfd8c65a92e)

choose your index name and edit other settings if you want , in my case i will go with default settings after done with index name 

![image](https://github.com/user-attachments/assets/3553cf17-4ab8-46be-a638-e6b6e5bdc2e4)

### Step 5 
## Downloading,installing and configurating the splunk universal forwarder in ubuntu virtual machine 

To download splunk universal forwarder, go to the free Trails and Downloads
and choose 64 bit .tgz file


![image](https://github.com/user-attachments/assets/490829e5-9429-47df-972e-c0066d1e97b5)

After completion of downloading splunk forwarder , open terminal and go to the downloads directory by typing "cd Downloads" then use following following command to unpack the content in current directory 
"tar xvzf <splunk forwarder name>" as shown in below.

![image](https://github.com/user-attachments/assets/243d807c-1458-44af-bad8-22e77ae05552)

move the splunk forwarder folder or directory to the /opt folder
Note:The /opt directory in Linux is used to store optional or third-party software that is not managed by the system's package manager.

![image](https://github.com/user-attachments/assets/44cfee9b-dc4f-4a62-8946-8d9ab85a0ae8)

creating a dedicated splunk user (or similar) is a good security best practice, though not strictly required. By default, Splunk Universal Forwarder runs as the user who installs or starts it, often root—which is not ideal for security.

![image](https://github.com/user-attachments/assets/10c938bf-12a2-45b5-b541-56db955ae0c8)

Change Ownership of Splunk Forwarder Directory as shown below:

![image](https://github.com/user-attachments/assets/19985bb9-ab7b-43d5-ada5-0385e265d9ed)

check the ownership of Splunk Forwarder Directory

![image](https://github.com/user-attachments/assets/6d8d41f1-87c1-431f-b4fe-f57340eccb56)

Use this command "./splunk start --accept-license"  to start the Splunk software for the first time, while automatically accepting the license agreement.
Note:it will ask for administrator username and password give them 

![image](https://github.com/user-attachments/assets/5eb0b9cb-2808-423f-a7a3-b98dc8ca16d3)

configure the splunk universal forwarder in ubuntu virtual machine to send data to the splunk server 
The command:./splunk add forward-server ip port is used to configure the Splunk Universal Forwarder to send data to a Splunk indexer (or intermediate heavy forwarder) tomdo this we need to login as splunk user.
Note: IP address(host os ip) and port(9997) of the receiving Splunk instance.
![image](https://github.com/user-attachments/assets/99c123c4-2711-4de1-b614-aa879c714166)

Use ./splunk add monitor /var/log -index indexname to monitor those logs

![image](https://github.com/user-attachments/assets/f8654ad8-66d9-411d-ad05-debad038b26d)


### step 6

check the splunk server to know that splunk universal forwarder sending data to the  splunk server.

![image](https://github.com/user-attachments/assets/b681bcd8-c8bf-42da-9d54-1c4626a44fff)

 Click on the Search and Reporting and in search field type index="ubuntu"

 ![image](https://github.com/user-attachments/assets/ade50675-4b17-4fc7-93af-8f8da8a6af00)

 ![image](https://github.com/user-attachments/assets/aad910a7-02fc-491b-b739-0ce6d42f5f59)

### step 7
In this step I choose to create a basic dashboard in splunk server related to failed login attempts. Wrote an spl search query to know the authentication failure's and click on the save as New dashboard:

![image](https://github.com/user-attachments/assets/d68d0f90-6a4b-405e-a021-29f6abfbedfd)


Give Dash Board title, choose CLassic Dashboards and click on the Save to dashboard

![image](https://github.com/user-attachments/assets/dc9fecf4-795c-4f82-a315-3fab0c885599)

Go to the dashboards tab and select on the Dashboard , which is created earlier  
 
![image](https://github.com/user-attachments/assets/0a0b2f96-cda7-4941-afe2-71f7e1a6d86c)

### Step 8
### Creating a real-time alert to monitor the client in real time. (I created an alert for authorization failures occurring in real time in this step.)

Write a search query to detect authentication failures, then click on the 'Save As' tab and select the 'Alert' option.

![image](https://github.com/user-attachments/assets/707af302-250b-43b9-a97d-f4abc79a3f5b)

Edit the alert as per your needs and click on save. I have edited it as follows:

![image](https://github.com/user-attachments/assets/264258ea-da07-4b6d-ae81-1cdf117ac780)

we have done with creation of Real-time alert

![image](https://github.com/user-attachments/assets/3114ce43-d88e-4ebc-b67c-ce5914b0e84b)

when i gave wrong password to login into the ubuntu virtual machine (snort user):
![image](https://github.com/user-attachments/assets/7f06fe89-afa4-48ff-aca5-324f4183fcc8)

it will give us a real-time alert:

![image](https://github.com/user-attachments/assets/9b19d671-3b45-42e4-a73a-0c419de46d02)

### Step 9
In this step, I will Attempt unauthorized access to the target machine (Ubuntu virtual machine ) using Kali Linux (attacking machine).
Note: snort is the user , which was created in ubuntu.You can see my attacking virtual machine ip address below:

![image](https://github.com/user-attachments/assets/fe248df4-fdc1-4dd6-aed7-7ad3b55c5a4e)

The command "ssh user@ip_address" is used to initiate an SSH (Secure Shell) connection to a remote machine , which i have used below to get access to the target machine with wrong password.

![image](https://github.com/user-attachments/assets/b75258b8-a3a5-4ef5-b30c-531994ae4cff)

### Step 10 
## Results 

when we click on the activity we can see triggered  alerts click on that to see Real-Time Alerts 
![image](https://github.com/user-attachments/assets/af15d67c-3be4-4b32-8268-d49218b6ab93)

When we navigate to the Dashboard we can see rhost(attacking machine) ip address:

![image](https://github.com/user-attachments/assets/183f6dba-faa0-401f-b128-4acb4c4933a4)

### STEP 11
### Integrating snort with the real-time monitoring SIEM solution starts from here after installation of snort in both server and client.

Install the snort app in splunk server by click on the app and then find more apps as below:

![image](https://github.com/user-attachments/assets/619bb2eb-3a64-4a8c-bac1-22dd92d3803a)

search for snort app and click on install as follows:

![image](https://github.com/user-attachments/assets/5e398145-dc7f-48bc-957e-353e110f27f6)

it will ask for credentials and click on agree and install

![image](https://github.com/user-attachments/assets/a2f4a947-5699-4f9d-9964-00c9e0dba31f)
we are done with the installation of snort in splunk server
![image](https://github.com/user-attachments/assets/86aa1805-173b-4bf9-86fe-266b6bc3a3df)

We can see Snort Alert for Splunk app in the home of the server.

![image](https://github.com/user-attachments/assets/e306a0b5-0cd2-4606-b278-352e6182e547)

When we click on that we can see zero traffick , because we are not done with the installation of snort in ubuntu virtual machine and integration of it with splunk universal forwarder.

![image](https://github.com/user-attachments/assets/878ab85a-9601-41bf-8bfb-6d065b10196f)

### STEP 12
## Install the snort app in Ubuntu virtual machine 
The installation process for snort varies depending on the oprating system,Given below is a general guide for installing snort in ubutu operating systems.

sudo apt-get update
sudo apt-get upgrade -y
sudo apt install snort 
![image](https://github.com/user-attachments/assets/4e2f76fa-484e-410c-8e5c-a545bfd53fc9)

To confirm it's installation use the command "sudo snort -V"
![image](https://github.com/user-attachments/assets/f5683324-2413-4e26-b0fb-769950f06752)

or use "sudo service snort status"

![image](https://github.com/user-attachments/assets/67aba278-c120-438a-b6b9-8675d2e9c931)

Stop the snort sevices temporarily

![image](https://github.com/user-attachments/assets/23992bcc-cdc4-42dc-a328-a3cda52d7893)

### STEP 13

## Configuring Snort and integrate it with the Universal Forwarder to send data to the Splunk server
Use the following command's
sudo su
cd /opt/splunkforwarder/etc/apps/search/local
ls (you will see inputs.conf)
cat inputs.conf

![image](https://github.com/user-attachments/assets/34b01eb2-29c2-446f-9375-bc6aa18092c2)

Open another terminal and search for snort.log, where Snort stores its logs,by using following commands:
cd /var/log/snort
ls
we can see snort.log file 
![image](https://github.com/user-attachments/assets/70361b55-449a-463c-afe7-ff34c1b4ae4a)










  


  
  
  
  
  




