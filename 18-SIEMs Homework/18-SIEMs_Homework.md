## Brian C Williams

## Unit 18 Homework: Lets go Splunking!

### Scenario

You have just been hired as an SOC Analyst by Vandalay Industries, an importing and exporting company.
 
- Vandalay Industries uses Splunk for their security monitoring and have been experiencing a variety of security issues against their online systems over the past few months. 
 
- You are tasked with installing new Splunk apps and developing searches, custom reports and alerts to monitor Vandalay's security environment in order to protect them from future attacks.


### System Requirements 

You will be using the Splunk app located in the Ubuntu VM.


### Your Objective 

Utilize your Splunk skills to design a powerful monitoring solution to protect Vandaly from security attacks.

After you complete the assignment you are asked to provide the following:

- Screen shots where indicated.
- Custom report results where indicated.

### Topics Covered in This Assignment

- Researching and adding new apps
- Installing new apps
- Uploading files
- Splunk searching
- Using fields
- Custom reports
- Custom alerts

Let's get started!

---

## Vandalay Industries Monitoring Activity Instructions

### Step 1: Monitoring Vandalay's Web Servers

**Background:**  As the worldwide leader of importing and exporting, Vandalay Industries has been the target of many adversaries attempting to disrupt their online business. Recently, Vandaly has been  experiencing DDOS attacks against their web servers.

**Task:** Install and configure a new Splunk App called **Network Toolkit** to monitor Vandaly's web servers `198.153.194.1` and `198.153.194.2`.  As a note, **Network Toolkit**  has many networking capabilities such as ping, traceroute, and speedtests.

1. In the Splunk app on your Ubuntu VM, find and install the add-on called **Network Toolkit** .
    
    - Note: You will need to use a personal Splunk account to install **Network Toolkit**. If you haven't signed up for a free Splunk account, sign up here: [https://www.splunk.com/page/sign_up?redirecturl=https://www.splunk.com/]

   - Note: You will likely have to restart Splunk when prompted.
         
2. After a successful install, select the new **Network Toolkit**  app from your list of available apps.

3. Select **Ping** >> and **Execute Ping** (leave the other fields as they are)

   - Enter in the following hosts one at a time:  `198.153.194.1` and `198.153.194.2` then click **Execute Ping**

4. Let the monitoring run and view the **results** page

5. Provide a screenshot of the results screen that displays the state of your web servers

    ![Image of q1](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Q1_ping%20Dec%2028%2017-46-28.png)
    
    ![Image of q1](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Q1_ping2%20at%20Dec%2028%2017-49-26.png)


Bonus: Run the speedtest and provide a screenshot of those results.

   The speedtest did not produce any activity when provding the IPs for the two servers.

   ![Image of speedtest](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Q1Bonus1-Dec%2028%2017-55-14.png)
   
   ![Image of speedtest](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Q1Bonus2%20Dec%2028%2017-56-05.png)
  
  **Running the speedtest with no IP supplied (I suppose no IP means the speedtest will test the Internet connection on my device) generated results.**
  
   ![Image of speedtest](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Q1Bonus3%20Dec%2028%2017-57-41.png)

### Step 2: The Need for Speed 

**Background**: Not only were web servers taken offline by a DDOS attack, but upload and download speed were also significantly impacted after the outage. Your networking team provided results of a network speed run around the time of the latest DDOS attack.

**Task:** Create a report to determine the impact that the DDOS attack had on download and upload speed. Additionally, create an additional field to calculate the ratio of the upload speed to the download speed.


1.  Upload the following file of the system speeds around the time of the attack.
    - [Speed Test File](resources/server_speedtest.csv)

2. Using the `eval` command, create a field called `ratio` that shows the ratio between the upload and download speeds.
   - Hint: The format for creating a ratio is: `| eval new_field_name = 'fieldA'  / 'fieldB'`
      
3. Create a report using the Splunk's `table` command to display the following fields in a statistics report:
    - `_time`
    - `ip_address`
    - `download_megabits`
    - `upload_megabits`
    - `ratio`
  
   Hint: Use the following format when for the `table` command: `| table fieldA  fieldB fieldC`

4. Answer the following questions:

    - Based on the report created, what is the approximate date and time of the attack?
         
         **The attack occurred on February 23rd at 9:30:00 AM. At that time, the upload and download speeds for both servers were extremely slow which indicates the DDOS attack consuming large amounts of upload and download bandwidth.**
         
         ![Image of attack](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/sped1.png)
         
         
    - How long did it take your systems to recover?
         
         **The systems recovered on February 23rd at 18:30:00 (6:30 PM), nine hours after the DDOS attack occurred. Upload and download bandwidth speeds increased to there pre DDOS attack rates. The ratio is 0.2 which also indicates a fully recovery.**
         
         ![Image of recovery](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/sped3.png)
       
         **It appears that the ratios are 0.2 when the upload and download bandwidth speeds are at their highest and lowest values.**
         
         ![Image of ratios](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/ratios.PNG)
         
         
Submit a screen shot of your report and the answer to the questions above.

![Image of report](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/sped.PNG)

### Step 3: Are We Vulnerable? 

**Background:**  Due to the frequency of attacks, your manager needs to be sure that sensitive customer data on their servers is not vulnerable. Since Vandalay uses Nessus vulnerability scanners, you have pulled the last 24 hours of scans to see if there are any critical vulnerabilities.

  - For more information on Nessus, read the following link: https://www.tenable.com/products/nessus

**Task:** Create a report determining how many critical vulnerabilities exist on the customer data server. Then, build an alert to notify your team if a critical vulnerability reappears on this server.

1. Upload the following file from the Nessus vulnerability scan.
   - [Nessus Scan Results](resources/nessus_logs.csv)

2. Create a report that shows the `count` of critical vulnerabilities from the customer database server.
   - The database server IP is `10.11.36.23`.
   - The field that identifies the level of vulnerabilities is `severity`.
   
   ![Image of critial DB](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Screenshot%20at%20Dec%2028%2021-51-09.png)
   ![Image of DB report](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Screenshot%20at%20Dec%2028%2021-58-52.png)
   
3. Build an alert that monitors every day to see if this server has any critical vulnerabilities. If a vulnerability exists, have an alert emailed to `soc@vandalay.com`.

![Image of aleart](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Screenshot%20at%20Dec%2028%2021-47-27.png)
![Image of aleart](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/Screenshot%20at%20Dec%2028%2021-47-55.png)
![Image of aleart](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/q3.b.png)
![Image of aleart](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/q3.c.png)

### Step 4: Drawing the (base)line

**Background:**  A Vandaly server is also experiencing brute force attacks into their administrator account. Management would like you to set up monitoring to notify the SOC team if a brute force attack occurs again.


**Task:** Analyze administrator logs that document a brute force attack. Then, create a baseline of the ordinary amount of administrator bad logins and determine a threshold to indicate if a brute force attack is occurring.

1. Upload the administrator login logs.
   - [Admin Logins](resources/Administrator_logs.csv)

2. When did the brute force attack occur?
   - Hints:
     - Look for the `name` field to find failed logins.
     - Note the attack lasted several hours.
     
     **The brute force attack occurred on February 21 at 4 AM thru 8 AM. It ended on the same day at 9 AM.**
     
     ![Image of attack](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/bf1.PNG)
     ![Image of attack](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/bf2.PNG)
      
3. Determine a baseline of normal activity and a threshold that would alert if a brute force attack is occurring.
   
   **A baseline of normal activity is 11-12 failed login attempts. A threshold of 25-50 failed login attempts would identify a brute force attack.**
    
    ![Image of baseline](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/BL.PNG)
    
4. Design an alert to check the threshold every hour and email the SOC team at SOC@vandalay.com if triggered. 

![Image of baseline](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/bfa.PNG)
![Image of baseline](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/bfa2.PNG)
![Image of baseline](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/18-SIEMs%20Homework/images/bfa3.PNG)


 
 
