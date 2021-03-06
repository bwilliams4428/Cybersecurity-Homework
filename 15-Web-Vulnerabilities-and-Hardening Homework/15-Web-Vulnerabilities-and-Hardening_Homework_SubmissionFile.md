**Brian C Williams**

## Unit 15 Submission File: Web Vulnerabilities and Hardening


### Part 1: Q&A

#### The URL Cruise Missile

The URL is the gateway to the web, providing the user with unrestricted access to all available online resources. In the wrong hands can be used as a weapon to launch attacks.

Use the graphic below to answer the following questions:

| Protocol         | Host Name                 | Path                   | Parameters               |
| ---------------- | :-----------------------: | ---------------------- | ------------------------ |
| **http://**      | **`www.buyitnow.tv`**     | **/add.asp**           | **?item=price#1999**     |


1. Which part of the URL can be manipulated by an attacker to exploit a vulnerable back-end database system? 

	**Parameters**

2. Which part of the URL can be manipulated by an attacker to cause a vulnerable web server to dump the `/etc/passwd` file? Also, name the attack used to exploit this vulnerability.

	**Path**
   
3. Name three threat agents that can pose a risk to your organization.

	 * **Hacktivist**
	 * **Criminal hacker**
	 * **Disgruntled employee**

4. What kinds of sources can act as an attack vector for injection attacks?

 	* **HTML forms**
	* **HTTP headers**
	* **Web application**
	* **Email headers**
	* **Web browser**

5. Injection attacks exploit which part of the CIA triad?

	**Confidentiality** 

6. Which two mitigation methods can be used to thwart injection attacks?
		
	* **Input validation**
	* **Input sanitization**
____

#### Web Server Infrastructure

Web application infrastructure includes  sub-components and external applications that provide  efficiency, scalability, reliability, robustness, and most critically, security.

- The same advancements made in web applications that provide users these conveniences are the same components that criminal hackers use to exploit them. Prudent security administrators need to be aware of how to harden such systems.


Use the graphic below to answer the following questions:

| Stage 1        | Stage 2             | Stage 3                 | Stage 4              | Stage 5          |
| :------------: | :-----------------: | :---------------------: | :------------------: | :--------------: |
| **Client**     | **Firewall**        | **Web Server**          | **Web Application**  | **Database**     |
   
   
1. What stage is the most inner part of the web architecture where data such as, customer names, addresses, account numbers, and credit card info, is stored?

	**Stage 5 Database**

2. Which stage includes online forms, word processors, shopping carts, video and photo editing, spreadsheets, file scanning, file conversion, and email programs such as Gmail, Yahoo and AOL.

	**Stage 4 Web Application**

3. What stage is the component that stores files (e.g. HTML documents, images, CSS stylesheets, and JavaScript files) that's connected to the Internet and provides support for physical data interactions between other devices connected to the web?

	**Stage 3 Web Server**

4. What stage is where the end user interacts with the World Wide Web through the use of a web browser?

	**Stage 1 Client**

5. Which stage is designed to prevent unauthorized access to and from protected web server resources?

 	**Stage 2 Firewall**

----


#### Server Side Attacks

In today’s globally connected cyber community, network and OS level attacks are well defended through the proper deployment of technical security controls such as, firewalls, IDS, Data Loss Prevention, EndPoint and security. However, web servers are accessible from anywhere on the web, making them vulnerable to attack.

1. What is the process called that cleans and scrubs user input in order to prevent it from exploiting security holes by proactively modifying user input.

	**Input sanitization**

2. Name the process that tests user and application-supplied input. The process is designed to prevent malformed data from entering a data information system by verifying user input meets a specific set of criteria (i.e. a string that does not contain standalone single quotation marks).

	**Input validation**

3. **Secure SDLC** is the process of ensuring security is built into web applications throughout the entire software development life cycle. Name three reasons why organization might fail at producing secure web applications.

	* **Lack of enforcement of secure coding standards**
	* **Expensive to implement**
	* **Developers not able to produce secure code**

4. How might an attacker exploit the `robots.txt` file on a web server?

	**The robots.txt file has entries that allow and/or disallow a search engine bot access to specified directories. Directories and files 	  that are disallowed in the robots.txt may contain important data that an attacker can target.**

5. What steps can an organization take to obscure or obfuscate their contact information on domain registry web sites?

	**An organization can enable whois privacy and/or utilize GDPR which all registrars are obligated to offer since ICANN adopted it in 2018**
   
6. True or False: As a network defender, `Client-Side` validation is preferred over `Server-Side` validation because it's easier to defend against attacks.

   - Explain why you chose the answer that you did.

	 **False. Server-side validation is much more important than client side validation. Client side validation can be easily bypassed by the  	      user disabling JavaScript in their web browser. Server side validation cannot be easily bypassed on the client side. Server side         	          validation can verify user input from the client, deem the input valid or invalid and alter the input if includes malicious or suspcious     	          characters.**
____

#### Web Application Firewalls

WAFs are designed to defend against different types of HTTP attacks and various query types such as SQLi and XSS.

WAFs are typically present on web sites that use strict transport security mechanisms such as online banking or e-commerce websites.

1. Which layer of the OSI model do WAFs operate at?

	**Layer 7 Application**

2. A WAF helps protect web applications by filtering and monitoring what?

	**HTTP and HTTPS traffic**

3. True or False: A WAF based on the negative security model (Blacklisting) protects against known attacks, and a WAF based on the positive security model (Whitelisting) allows pre-approved traffic to pass.

	**True**
____

#### Authentication and Access Controls

Security enhancements designed to require users to present two or more pieces of evidence or credentials when logging into an account is called multi-factor authentication.

- Legislation and regulations such as The Payment Card Industry (PCI) Data Security Standard requires the use of MFAs for all network access to a Card Data Environment (CDE).

- Security administrators should have a comprehensive understanding of the basic underlying principles of how MFA works.

1. Define all four factors of multifactor authentication and give examples of each:

   **- Factor 1: Single factor authentication - "Something you know" - A user gains access to a system or asset using only one category of  	  	 credentials such as password(password, PIN, challenge phrase) based authentication.**

   **- Factor 2: Two factor authentication - "Something you have" -A user gains access to a system or asset using two different categories of 	  	 credentials such as a password and a device with that provides user authentication such as smartphone with an authenticatior app or a USB 	  key fob such as a Yubikey.**
   
   **- Factor 3: Three factor authentication "Something you are" - A user gains access to a system or asset using three different categories of  	credentials such as a password, device with authentication software and a biometric credential such as a fingerprint or voice sample.**

   **- Factor 4: Four factor authentication - A user gains access to a system or asset using four different categories of credentials such as a   	 password, device with authentication software, biometric credentials such as a fingerprint or voice sample and time based authentication or      	 location credential such as a tracking microchip embedded in your skin or GPS tracker on your person.**
   
2. True or False: A password and pin is an example of 2-factor authentication.

   **False. A password and pin are both forms single factor authentication that provide no added layer of security.**
   
3. True or False: A password and `google authenticator app` is an example of 2-factor authentication.

   **True**
   
4. What is a constrained user interface? 

   **An interface that restricts user access to specific functions and system resources. A restricted shell and an ATM machine are examples of         	    constrained interfaces.**
----
____

### Part 2: The Challenge 

In this activity, you will assume the role of a pen tester hired by a bank to test the security of the bank’s authentication scheme, sensitive financial data, and website interface.


#### Lab Environment   


### The Challenge Instructions

#### Challenge #1

Your first mission is to break the authentication scheme. There are a number of ways to accomplish this task.

- **Hint #1**: Sometimes, form fields are shy!

- **Hint #2**: Find the hidden JavaScript.

- **Hint #3**: You can appened `source?source=true` to the URL to read the source code. 

Please include a screenshot here of the hidden JavaScript:
![Image of Challenge1](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/15-Web-Vulnerabilities-and-Hardening%20Homework/images/Challenge%201.PNG)

![Image of Challenge1.2](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/15-Web-Vulnerabilities-and-Hardening%20Homework/images/Challenge1.2.PNG)


#### Challenge #2

Next, steal all of the credit card numbers from the database. 

- **Hint #1**: Sometimes cookies wear different clothes to change their appearances.

- **Hint #2**: Break your way into the conversation and inject your own ideas.

Please include a screenshot here of all the credit card numbers from the database. 

![Image of Challenge2](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/15-Web-Vulnerabilities-and-Hardening%20Homework/images/challenge2.1.PNG)

![Image of Challenge2](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/15-Web-Vulnerabilities-and-Hardening%20Homework/images/chALLENGE23.PNG)

![Image of Challenge2](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/15-Web-Vulnerabilities-and-Hardening%20Homework/images/Challenge%202.PNG)

#### Challenge #3

Your final act is to deface the website using command injection. Follow the walkthrough below to help you get started. 

Please include a screenshot of the defaced website. 
	
     
      tcp && sed -i '1s/^/You have been hacked by Brian Williams Pay me now /' /var/lib/tomcat6/webapps/WebGoat/webgoat_challenge_guest.jsp 
      
![Image of Challenge3](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/15-Web-Vulnerabilities-and-Hardening%20Homework/images/Challenge333.PNG)

![Image of Challenge3](https://github.com/bwilliams4428/Cybersecurity-Homework/blob/main/15-Web-Vulnerabilities-and-Hardening%20Homework/images/Challenge3n.PNG)
     
---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
