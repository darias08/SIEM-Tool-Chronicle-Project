<h1>SIEM-Tool: Chronicle Project</h1>

<h2>Description</h2>

In this project, I will be using a cyber security SIEM tool called [Chronicle](https://cloud.google.com/chronicle/docs/overview), a cloud-native tool, to investigate a security incident that involved a phishing attack. The goal of this project is to showcase my knowledge of using this tool and how effective it is for me to identify threats.


<h2>Scenario</h2>

You are a security analyst at a financial services company. You receive an alert that an employee received a phishing email in their inbox. You review the alert and identify a suspicious domain name contained in the email's body: `signin.office365x24.com`. You need to determine whether any other employees have received phishing emails containing this domain and whether they have visited the domain. You will use Chronicle to investigate this domain.

<h2>Project Walkthrough:</h2>

<p align="center">
Launching Chronicle: 
<br/>
  
![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/9ac71420-6237-4b21-90b1-3e74a7a89f02)

<br />
</p>

<p align="center">
  I inputted the domain signin.office365x24.com in the domain search to find log entries: 
<br/>
  
![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/549b5850-c0bb-43c0-b22c-76a5c421e3a6)

<br />
</p>

</p>

<p align="center">
  I identified that this domain does contain 1 malicious attribute.
<br/>
  
  ![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/852f6f0c-e5aa-44e3-936b-07d28a56da5c)
  ![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/8d53b447-9f7e-4ab0-8e73-ed8a5b98369d)


<br />
</p>

<p align="center">
  After looking a little deeper within the logs, I found out that there is a Top-Level Domain that is connected to this.
<br/>
  
![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/e1a6206a-317d-4809-967b-d757e65ef6ae)

<br />
</p>

<br />
</p>

<p align="center">
  This top-level domain contains 5 malicious viruses. 
<br/>
  
![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/4ce794e0-1cfa-4cdb-8d11-3a8d58c511eb)

<br />
</p>

<p>
  Now that I identified these domains are malicious. It's time for me to find out which employee has clicked on this phishing link and which employees it has sent it to. 
   On the left-hand side of the dashboard, shows the timestamps of when the malicious attack occurred. It contains all the users that have received this attack from this malicious domain.
</p>
<br/>
  
![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/e7e37341-da9a-408d-9178-81dddf5f2430)
<br />

<p align="center">
  
  After reviewing, I was able to identify two methods that were found in each employee. The `GET` method means that the employee received the domain, but didn't do anything with it. The `POST` method, however, indicates that the employee did something with that domain. The two employees I see that got a `POST` method was Emil Palmer and Ashton Davidson.
<br/>

![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/ad77f240-fc36-423c-8546-50202acc2a99)
![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/c66621fb-940b-48b5-ae61-311ab9b1aff7)


<br />
</p>

<p align="center">
  
  Now that I found out which employees were involved in this attack. I wanted to figure out where this attack came from. I see in the **Resolved IPS** tells me the list of IP addresses this attacker used. The two I see are `104.215.148.63` and `40.100.148.63`.

  ![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/ef32cbdc-53e4-4a64-918d-cf6f9d40ecf3)

<br/>
<br />
</p>

<p align="center">
  
  First I checked the `40.100.174.34` and see what kind of details I can find there. It looks like this incident happened on January 31st, 2023 and the same users were involved in this attack (Emil Palmer and Ashton Davidson).

  ![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/1113ef4c-d7a1-4635-9aba-ee7b8aaa5dc1)


<br/>
<br />
</p>

<p align="center">
  
  I was also able to find a different type of domain that is linked with this IP address `40.100.174.34`. In the **Domain Section**, I see `signin.accounts-gooqle.com` which has a similar phishing attack as the `signin.office365x24.com`.

  ![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/5422b109-0c9b-4c5a-8d66-91f9430b44a6)

<br/>
<br />
</p>

<p align="center">
  
  The attacker tried to use the `signin.accounts-gooqle.com` at these two employee users (Amir David and Warren Morris). However, there was nothing to be concerned about the user's credentials being compromised since the response was a `GET` and nothing else.

  ![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/929275cf-7718-4cf7-86ff-9030e9e36e38)

<br/>
<br />
</p>

<p align="center">
  
  Next, I am evaluating the next IP address that was found by the attacker's IP `104.215.148.63`. This IP has some similar phishing attacks as what happened to the previous but this time this attack had a **confidence**: low status. Meaning it wasn't as effective of an attack compared to the first one which was high. 

  ![image](https://github.com/darias08/SIEM-Tool-Chronicle-Project/assets/58616895/c0256296-2fe7-4f46-b547-13a7763a9221)


<br/>
<br />
</p>

<h2>Incident Report</h2>

| **Date**: July 15, 2023    | Entry #1 |
| ------ |  :---  |
| **Description** | Investigated a phishing attack that occurred at a Financial Service Company organization. |
| **Tool(s)** used |  Chronicles |
| **The 5 W's** | <br> Capture the 5 W's of an incident: <br> <br> **1.) Who** caused the incident? Ashton Davidson and Emil Palmer were the ones responsible for the incident. </br> <br> **2.) What** happened? Two employees clicked on a phishing email link that contained malicious malware inside. </br> <br> **3.) When** did the incident occur? This incident first occurred on January 31, 2023, and the last two were on July 8th, 2023, and July 9th, 2023. </br> <br> **4.)** **Where** did the incident happen? It took place at an organization called, "Financial Service Company".  </br> <br> **5.) Why** did the incident happen? Not enough evidence as to why this incident occurred. I am not sure what was the attacker's goal, but I am assuming it has to do with retrieving money since they are targeting a financial service company. </br> <br> </br>|
| **Additional Notes** | <br> **1.)** The suspicious domain that was provided by the employee is `office365x24.com`</br> <br> **2.)** After viewing that domain on Chronicle security from Google. I found that this domain has 5 malicious viruses. </br>  <br> **3.)** It also contained two subdomains that are associated with the main domain.  `login.office365x24.com` and `signin.office365x24.com`. </br> <br> **4.)** The `login.office365x24.com` has no malicious virus within, but the `signin.office365x24.com` has one malicious virus. </br>  <br> **5.)** In the `signin.office365x24` there are two Resolved IPS: `40.100.174.34` and `104.215.148.63`, which is from the attacker’s IP address. </br> <br> **6.)** The IP address of `40.100.174.34` has  2 user accounts that had a successful login attempt from this suspicious IP address. Both user accounts received a `POST` /login.php response.</br>  <br> **7.)** I noticed the `40.100.174.34` and `104.215.148.63` has a domain name of `signin.accounts-gooqle.com` ⇐== This domain doesn’t seem like a legit domain name and I think the victims got tricked into thinking it’s real.</br>  |
| **Reflections/Notes: Record additional notes.**| After analyzing and collecting this information, I am able to provide some good points on how to prevent this attack. I would suggest making sure that employees check if the email is legitimate before clicking on it. For example, both domains are misspelled like the `sigin.accounts-gooqle.com` has Google spelled wrong and Microsoft 365 sign-in has `signin.office365x24.com` with a `x24` after 365. If the user was able to identify the misspelled domain names from this phishing attack, then this could have been prevented. Another suggestion to prevent this attack is to have a **multi-factor** authorization which reduces the chance of the attacker getting their credentials. It makes the attacker have to retrieve an authorization code from their cell phone which prevents the attacker from logging into their account.  Lastly, I would recommend having an **anti-virus** software installed which helps identify any suspicious links or files in an email and remove them before the attacker exploits the user or machine. Having these security recommendations will greatly secure your organization's credentials or information from attackers.|

<!--
 <br> **1.)** The email that was provided by the employee contains this email domain `office365x24.com` </br> <br> <br> **2.)** After viewing that domain on Chronicle security from Google. I found that this domain has 5 malicious viruses. </br> **3.)** It also contained two subdomains that are associated with the main domain.  `login.office365x24.com` and `signin.office365x24.com` <br> **4.)**  The `login.office365x24.com` has no malicious virus within, but the `signin.office365x24.com` has one malicious virus. </br> **5.)** In the `signin.office365x24` there are two Resolved IPS: `40.100.174.34` and `104.215.148.63`, which is from the attacker’s IP address </br> 
-->
