 ![TibAct Logo](https://drive.google.com/file/d/16nbVMM-HJYwD7KiGb9icO0y9mchdDFiQ/view?usp=sharing)

# **A Tibet Action training guide for online security, understanding malware, securing your communications & mobile security.** #


## Version 1.0 ##

**Fall 2016**

* **Section 1** : Understanding how the Internet works, basic concepts and best practices

* **Section 2** : Understanding risks, vulnerabilities and capacities

* **Section 3** : Malware and targeted malware - problems and solutions

* **Section 4** : Targeted website attacks - problems and solutions

* **Section 5** : Responding to compromises & mitigation

* **Section 6** : Mobile security - basic device security & app security

 
## Section 1 – Understanding how the Internet works, basic concepts and best practices ##
 
### I. Internet 101

Goals: 
-	To understand the basics of how the internet works and understand what each of the layers in the network does.
-	To know the process from when you send a request to open a website to how it is finally displayed on your browser.

Key concepts: Even a simple act such as typing the address of a website you want to see into your computer browser means information is transmitted, in many steps, to many different people/authorities often around the world. At each step along the way, information about you is visible to anyone on the network between you and the information you are requesting.

Advanced prep:
: 1. Wireshark - Capture the network traffic. (For advanced training, if needed)
: 2. Etherape: To show a visual representation of all connections being made from local network.
 
Show: Cyber Super Hero video (Tibetan Version)
 
> Question: What is an IP address?
> > Explain: The concept of an Internet Protocol (IP) address using the example of a fixed street address for a house or business.
 
> Question: What is DNS(Domain Name System)?
> > Explain: Use the example of a phonebook on your mobile device which automatically translates a name into a phone number while dialing.
 
> Question: How is a website displayed on your browser? How does your request fetch and bring the website back to you?
 
[Based on the following steps, an activity can be arranged or explained depending on the audience.]
  
Before going into internet security related topics, be it connecting from your mobile phone or computer, it’s useful to first understand how the internet works.
 
Have you ever wondered what happens after you type a domain name and click the Enter button to before the website appears on your screen in a matter of few seconds?
 
There are several layers of network that a query goes through back and forth when you submit from your computer or phone to when the site appears on your screen and let’s explain all these layers step by step.

To see how many hops(steps) it takes to go to website, you can use a traceroute website to see the number of hops such as http://network-tools.com/

Sample Traceroute from Dharamsala to Cybersuperhero.net
 

 
**For the purpose of understanding this, let’s say, you are getting your internet/data service from China Mobile.**
 
* __Step 1__ : You, the user, wants to open a website, aliyun.com from your computer/mobile phone. So you typed in the domain ‘aliyun.com’ in the browser and clicked on the button.
 
* __Step 2__ : From here the request first go through your Local Area Network or the LAN, the router at your home or at the cyber cafes you visit, in the public library or at the hotels or restaurants, etc. that relays internet connection to your device.
        	
* __Step 3__: Then, the request goes through the Internet Service Provider or the ISP, the companies that provide internet. (China Mobile is one of the major Chinese ISPs but there are also local ISPs or small players that distributes internet subscribed from these major ISPs at local level)
 
* __Step 4__: The ISP checks its Domain Name Server or DNS, in this case China’s root server for the domain, www.aliyun.com’s IP address which is 42.120.158.67
 DNS is the system that connects the domain name, www.aliyun.com, to it’s unique IP address and from there on, the request is transmitted along with the IP address. It’s like a phone book. There are only limited root servers in the world who have ultimate control over the DNS and China is running its own. ISPs could also have their own local DNS
 
* Step 5: This step may not apply for websites hosted on Chinese server. For all other websites, the request goes through the Internet Backbone. This is the physical bundle of fiber optic wires connecting the global network, the central network made of many large networks which are interconnected with each other.
 
* __Step 6__: The request is then sent to the Web Server that hosts the website. (In this case, Aliyun has it’s own server)
 
* __Step 7__: The server finally takes the request internally to the website’s dedicated server parked on the IP address, 42.120.158.67
 
* __Step 8__: The response to your request is sent back through the same channel and finally appears on your screen.
 
Each of these channels are run by various companies and governments and have the capability to monitor your activities at each step if the website is not encrypted, i.e. if it is not SSL certified and has no HTTPS
 
If you want to look for IP addresses of other websites that you visit, you can go to [getit.com](https://getit.com).
 
Let’s say you want to check the IP address of a website [korawa](https://Korawa.com)

* __Step 1__: Type the domain name of the website eg. korawa.com, gdqpzhx.com or any other website.
  
* __Step 2__: Type the characters on the right in the form
 
* __Step 3__: Click on Submit
 
* __Step 4__: Check your result.
  
The result will show the website’s IP address, the web server and where it’s hosted with some other information.
 
In case you only wish to know the IP address, you can also visit the site:
https://www.site24x7.com/find-ip-address-of-web-site.html
 
Show: How the Internet works video at the end of the first session as it gives good visualization of a web page being requested in the UK and traveling from US to UK with IP addresses, DNS lookup and packets being distributed.
 
How the Internet works
http://www.wimp.com/internetworks/
Additional resources:
How the DNS works
http://youtu.be/2ZUxoi7YNgs *This little cartoon illustrating how DNS works is likely too in-depth for our basic trainings but a good resource to have on-hand.
 
 
 
### II. HTTP and HTTPS

Goals: 
-	To understand the basics and importance of SSL encryption on the Internet.
-	To know how to look for SSL verification when visiting websites online. 

Key concepts: SSL is meant to provide both privacy and verification of website identities online.
 
Advanced preparation:
1.     Open browser & load “SSL Certificate Explained”: http://youtu.be/SJJmoDZ3il8
2.     Prepare prop – Depending on the activity:
a.     Car Activity: An open Jeep with a passenger, a car with black tinted windows.
b.     Postcard: Post Card, Envelope, Stamp.
c.     Box: A box with a lock
 
Show: Tibet Action’s HTTPS video with Postcard to explain HTTP vs HTTPS
 
Activity: Postcard - Get a few volunteers and have one of them write a message on the postcard and address it to one of the other volunteers. Make sure they write their return name and address too. Have the “sender” and “receiver” stand at opposite ends of the room. Based on the same ideas presented in the Internet 101 video, explain how  there are many stops along the way when you want to send a simple email message from one person to another. Have the people in the middle of the room be the hops along the way and have them pass the postcard from one to another and read the message out loud as they do. Emphasize: Not using HTTPS on either side of the transaction means that your message is as open to be read/monitored as if it was written on a postcard.
 
1) SSL Encryption
 
HTTP vs HTTPS - This classic explanation using a metaphor of roads/highways is general enough for us to talk about how information travels “in the clear”, or through encrypted channels, and why this matters - i.e. transmitting passwords securely, having private communications - emails, chat messages etc. - as well as the privacy of what we are actually viewing online.
 
Explain: There are two ways to send information online. One way is to send and receive information on HTTP roads and the other is to send and receive it on HTTPS roads.

- imagine you’re traveling on a highway, the Internet highway.
- you can either travel in a rikshaw, which is open and everyone can see inside - this is the HTTP road - and when you travel from your office to TCV, everyone can see you in there.
- or you can travel in a car with tinted windows where people watching can still see the car and that you are traveling on the road, but they can’t see into the car - this is the HTTPS roads.
 
The Internet was originally designed to be transparent and open and was built only with open HTTP roads where everyone and anyone could see all the information traveling to and from a destination. But as more and more commerce and private communications began to take place on the Internet, HTTPS roads (SSL capability) were built.
                                	
2) Identification
 
Explain: The second purpose of SSL or HTTPS is to verify that a website is what it seems to be.
 
Demonstrate: open Phayul.com, open Amazon.com
 
Explain: Websites can be spoofed. Unlike when you are in the real world and you can go to a physical location/address, like say for Phayul.com’s office in Dharamsala, when you are online/in cyberspace, you cannot verify that the address you requested is the actual address where you ended up. You may think you are going to Phayul.com, but really, when you type the address into your browser window your request could be hijacked, and you may be sent to a different DNS server. If there’s no HTTPS on the website you are visiting, you won’t ever know the difference. With HTTPS, it should tell you that something is wrong if the address you requested is not the place you are being taken to. [try to find example to demonstrate]
 
Show: SSL Certificate Explained https://youtu.be/SJJmoDZ3il8
Exercise: Have everyone open a laptop and find a website, besides ones we’ve used, to see if they use HTTPS or not. Try to find examples of sites that do and sites that don’t use HTTPS.
 
This is an example of a website that doesn’t have HTTPS and the browser should give a warning: https://web2.qq.com/
 
You can show participants EFF’s HTTPS Everywhere and they can download if they want: https://www.eff.org/https-everywhere
 
### III. Browsers

Goals: 
-	Understand how a browser window can make you vulnerable to viruses, online attacks and spying.
-	Understand how common browser features, like cookies, can be harmful and learn a few main mitigation tools and tactics.

Key concepts: 
-	Browsers are portals for potential attack.
-	Open-source software has benefits and risks.


Activity: Browser Choices
 
Step 1: Ask participants which browser they use most of the time.
Step 2: Ask them to divide up and stand/sit together into different groups based on their choices.
Step 3: Ask them to explain their choice of browser and as more and more different reasons come up, i.e. ease of use, first browser ever used, default/came with my computer, security features, add-ons, open-source code, etc., get them to discuss and defend their choices.

Explain:
-browser windows are like windows through which we look at the Internet (imagine the Internet/cyberspace is like outer space and we need special glass to view it through).
- some browsers use the most up-to-date technology with the most bullet proof glass etc. (Chrome), to protect us from threats that might exist out there in space (martians and such :).
- others are more old/clunky and not regularly kept up-to-date or created using the latest technological advances (Opera or whatever example we want to use as the worst browser)
- we always want to use a browser that is the most advanced and secure so that we are protected from any threats that might come at us from space (the Internet), and try to get into our home (computer) through the window (browser)

Explain: 
-	since the first step of visiting a website is to use a browser, making an informed choice as to which browser to use is one of the most important decisions.
-	Internet Explorer only updates when the entire Windows OS updates, whereas Chrome and Firefox don’t depend on a Windows update, they are constantly sending updates.
-	Chrome auto-updates, whereas Firefox requires the user to update manually or set up so that it auto-updates.
-	Firefox is open-source.
 
Question: What is Open Source?
Explain: Open source software is software whose source code is available for modification or enhancement by anyone. "Source code" is the part of software that most computer users don't ever see because it is kept strictly confidential by the companies that develop it; it's the code computer programmers can use to change how a piece of software works.
 
Discuss: Merits and demerits of open-source and general concept as we will be saying open-source a lot more as we go along with the training.
-   	Explain that open-source depends on the community behind it. Just because it is open source, doesn’t mean that it is without vulnerabilities.
-   	Explain that Firefox, Ubuntu and others have huge communities behind them.
-   	Explain the rationale behind the open-source belief system that software and Internet should be free and open to everyone.
 
1. History

Explain: Every browser, except a few including Incognito & Tor browser etc., saves all our browsing history unless we turn the history off. This is a convenient feature that allows browsers to remember web addresses we visit. But, if and when you lose your computer, or if someone else is able to take a look at your browser, it will show him/her all the information of the websites you have visited (in fact, if the browser is not cleaned from the beginning, it’ll show the history from time immemorial).
 
2. Cache

Explain: Each time we visit a website, it sends page information (mostly the page and the content, images etc.) to a temporary storage on our computer’s hard disk, unlike browser history which actually gets stored in the browser itself. These files are mostly images and pages of the website. Once this information is cached, it becomes much easier for users to quickly access the content the next time we visit the same website (it saves time). But also remember that, at times when there’s an update to a particular page of that website, when we visit that page, our browser may still show the old cached page instead of the updated one. For this reason, and for security reasons, you may wish to clear your Cache.
 
3. Cookies

Explain: Cookies are like personal assistants that websites appoint for us. It is a file that websites using cookies park in our browser directory that allows the website to watch our activity on the website. Cookies can be of two types, session and persistent cookies. Session cookies are temporary and will be removed after we close that website, whereas, persistent cookies are the ones that stay on and activate each time we open the website. Has it ever happened to you when you search or click on a product or a service on a website and thereafter, each time you visit that site, it shows promotions of that product or service? This is a work of cookies. Cookies may not be able to access the data on your computer, but they definitely track and follow your behaviour online and they could be used for spying on you.
 
* Although the above three features provide different services to either the user or the web owner, and although the information is parked at different locations on your computer, all these pieces together provide a lot of detailed information of the websites you have visited and your online activities.
  
4. Add-ons/Plugins or Extensions

Explain: Browsers have options to install add-ons or extensions mainly to enhance the users browsing experience. Most of them are good, but some could be malicious or could be used to steal your information. In order to prevent that from happening, one must choose extensions carefully. Install the plugins you know and need, and not just everything that looks nice and fancy.
 
In order to check what plugins you have already installed in your browser, you can go to the browser ‘Settings’ from the menu and choose ‘Extensions’. If you do not need the extensions you see, you can remove or disable them.

 
5. Private browsing

Explain: The easiest and the simplest option to maintain some level of privacy while browsing the Internet is to use Incognito window, a privacy option that most browsers provide. Although it is very important to note: going Incognito does not mean you will be anonymous while browsing online. Most web users don’t have the habit of clearing browsing history, so by simply using an Incognito browser window, users don’t have to worry about leaving traces of their activities online. Unlike a regular browser window, an Incognito window does not save your browsing history, cookies, etc. Once an Incognito window is closed, every activity that took place in that window will disappear. As mentioned above, an Incognito window is good only for wiping all traces of your online activity from the browser itself. It does not hide your activity in the network -  the websites you are visiting will still be able to see your location/IP address.
Recommendation: If you don’t want anyone to know about the websites you have visited and the information you have been looking at, and you don’t want websites you have visited tracking you, you should take these steps to make yourself more secure:
1) Browse in Incognito mode.
2) Use a proxy/vpn which we will explain in the coming lessons.
3) Use HTTPS-based websites only.

### IV. Understanding OS

Goals: 
-	Understand the key differences between Windows, Linux and Mac OS as they relate to security threats.


Key concepts: 
-	All OS are vulnerable to malware, but Windows is the target of the greatest number of known attacks because it is the most prevalent/popular OS. Also understand that just because they are more attacks doesn’t make a particular OS more vunerable. 
 
Windows Vs Linux Vs Mac
 
Explain: the difference between Windows, Linux and Mac. - each from the perspective of threat modeling which we learn about more in the next section, however explain here some risks associated with each of these OS based on individual use.

Windows is the most commonly used operating system [85% approx] in the world and, therefore, the greatest number of known attacks are designed to target Windows OS. 


Question: Do malware infect Windows only?
Explain: Malware looks for vulnerabilities and security holes in a computer and each OS mentioned above can have vulnerabilities. In terms of malware, we will go in details in the next section.
 
### V. Email

Goals: 
-	Understand that security should be a key priority for the choice of email account
-	Understand the security features, and main attack vectors, of Gmail.

Key concepts: 
-	2-step verification as the best security for Gmail, Facebook and other accounts
-	It is not safe to have random apps in use on your phone and computer. 
-	Users need to monitor what permissions apps have.

Advanced prep: Have login info for a Gmail account that you are okay with participants seeing displayed on the big screen.

Activity: Tech Choices

1.	Get the group to stand up and tell them you will ask them a question and they need to group themselves together by answer. They need to call out their answer and find others in the room who have the same answer. Question: What email provider do you use for your main email? 
2.	Let the group yell out to each other and locate others in the room who use the same email provider. If there are people who use more than one, tell them to find others who do too. Depending on the size of the group, those using multiple email providers may be able to find others using exactly the same combination of providers, otherwise, those using multiples can just stand together vs those using only one provider. This may take a few minutes only. Once they have found each other, ask them to stand in groups facing inwards, or towards you, so they can all see and hear each other.
3.	Ask each group to say what email provider they are using. Then focus in on one group - best to focus in on Yahoo or Hotmail or AOL users, if there are any - and ask: Why do you use ____ for your email?
4.	Use elicitive questions to get the following points to come out and go through each group one by one:
-   	“I signed up a long time ago / It was my first email account.”
-   	“Someone told me to use it, but I don’t know why it’s the best.”
-   	“Security features like HTTPS, 2-step verification, etc.”
-   	“I like the ethical stance of the company.”
-   	“It’s not a service based in China / It’s an American or European service.
5.	Wrap up with summaries of the different reasons why people end up using the email providers that they do and point out how often it is that we don’t consciously think about security and often use the first email provider they were ever exposed to or told about by a friend, etc. (Note: this may not be the case for some groups who may be very security-minded and so you may want to quietly survey the group before deciding to do this activity ).

Demonstrate: Gmail - Log in to the account and show the following features and functions:
 
Gmail security settings:
1. Explain what the Details button shows and how that can be used to see if your account has been accessed by someone other than you, and from where and when.
2. Check the Account Settings page for forwarding, filters and other features which have been used to quietly compromise accounts.
 
Ask: What is 2 step verification? If no response, explain the basic concept that to access your account you go through a 2 step verification process. The first step is to provide something that you know, which is your password, and the second step is to use something that only you have access to, which is your mobile device, to receive a code. These 2 steps help to verify that it’s really you. If you rely on only one step - like a password - it is not a truly secure method because, technically, anyone could “know” your password.
 
Show: 2-step video if needed:
https://www.youtube.com/watch?v=zMabEyrtPRg [English]
 
ASK: Specifically in the Tibet movement, why do we use 2-step verification? What is the importance of this kind of security measure? [Tell stories of compromises we have seen in the past].
 
Demonstrate: Log in with 2-step:
 
App passwords

Explain: 
- The need for app passwords
- Show apps that have access to your account in the security settings.

Ask: which apps you use and which you don’t? Try to find out what all the apps that have permission to your account represent.
 
Show: Other online accounts i.e. Facebook, Twitter, Dropbox. Depending on what people use, point out the security settings such as 2-step verification, if available, and other app permissions.
 
### VI. Best Practices
 
A. Attachments

Question: What are attachments?
Explain: Attachments can be any file that is attached to an original email. They contain various forms of file systems ranging from documents to photos to programs (i.e. .doc/.rar/.exe)
 
Question: How can attachments infect your computer?
Explain: An attachment such as Word document, PDF file, or another type of file, can be repurposed with malicious software added, and it can then be used to infect your computer. We will discuss in more detail in the malware section, but for now explain how malware uses vulnerabilities to exploit a system.
 
Question: How can you protect yourself from Attachments?

Show: Detach from Attachments Tibet Action Video
 
Emphasize: Detach from Attachments! Stop using attachments as that is the most common vector for attacking Tibetans with malware.
 
Emphasize: Use Google Drive – Use Google drive to preview rather than download attachments. Google drive has the functionality of being able to preview Word, Excel, Powerpoint, PDFs and images.
 
B. Links

Show: Think before you click! Tibet Action Video
https://www.cybersuperhero.net/thinkbeforeyouclick/

Explain: Website links are shared through email, WeChat and even through a text messages. Some links can take you to unknown websites with malicious scripts running on them, and others can even automatically download malware to your computer without your knowledge.
 
Demonstrate: How to check/verify links
 1. Hover your cursor over a link without clicking (be careful!) to preview the actual website address the link is directed to.
2. Read the links to understand whether it is spoofing a website or not.
 
Examples: REAL: google.com  VS. FAKE: g00gle.com

C. Software updates
 
Question: What is the purpose of an update? Why are updates important?
 
Explain: An update does the following:
1. Adds features
2. Removes outdated features
3. Updates drivers
4. Delivers bug fixes
5. Fixes security holes that have been discovered.
 
Explain: Security Holes - Any piece of software will, in time, eventually have security issues which can be then exploited to deliver malware or control a device. These security issues are discovered and fixed when they are found by the software developer or the OS, like Microsoft. The only way to fix these issues is to send out “updates” to all of the people/computers who are using that software. Regularly checking for and updating your computer software will fix the vulnerability and then it cannot be used, in the future, by an attacker to take control of your computer or device. Attackers rely on the fact that many people do not update their software or computer systems and therefore can be easily exploited.

Show: Don’t Wait, Update! Tibet Action video https://www.cybersuperhero.net/dont-wait-update/
 
D. Antivirus
 
Question: What is antivirus? How many of you use antivirus programs? Which ones?

Explain: Antivirus programs are used to prevent, search for, detect, and remove software viruses, and other malicious software like worms, trojans and adware. These are more generally termed as Malware. Antivirus companies generally have to deal with around 60,000 new pieces of malware that are created daily. So an antivirus program needs to be regularly updated, as known malware changes with each passing day.  If you only install an antivirus program once. and do not allow it to update itself daily, you are not protected against the 60,000 new malware programs discovered every day!
 
Limitations of antivirus programs - As explained before, an antivirus program discovers 60,000 new types of malware in a day, however, if the antivirus program you are using has not yet discovered the specific malware that is being used against you, then you are not protected. In the case of Tibetans, malware programs are sometimes created specifically for Tibetans and, as such, most antivirus are useless to stop these very specific ones.

Emphasize: It is good to use a malware program, as a basic safety precaution, to catch the 80% of known/regular attacks, however, you cannot depend on it to catch 100% of attacks. Only your good digital hygiene and behavior can help you stay safer.


 

## Section 2  : Understanding Risk, Vulnerabilities and Capacities ##
 
In this exercise we will introduce concepts around identifying risks and threats and have each participant identify specific threats, vulnerabilities and mitigation strategies.

Introduce the following concepts:
 
THREAT: Any type of possible attack against a person, system etc.

Examples: Office break-in. Arrest. Assault.
 
RISK: The probability and impact of a threat

Example: Contrast the risk of plane accident (low probability, high impact) with a car accident (high probability, high impact)
 
VULNERABILITY: Anything that makes it more likely for an attack to happen or result in greater damage.
 
CAPACITY: Any resource that improves security and prevents threats.
 
Activity: Have the group split into pairs. Each pair needs to come up with at least one example that links the following: Threat - Vulnerability - Capacity
 
Use these 2 examples.
 
| Threat|Vulnerability|Capacity
|------|----------|-----------|
|Office Break in|Poor quality locks on the doors| Install better locks. Alarm system|
 
|Threat	|Vulnerability	|Capacity
|---------|-----------|---------|
|Arrest and confiscation of mobile phone by authorities|Participating in direct action protest|Password lock screen Encrypted phone|
 
 
 
Discuss the examples generated within the group.
 
Harm Story Case Study
A member of Drewla (Tibetan human rights group), a young woman, decided to return to her family village in Tibet after working for two years for Drewla. She was arrested at the Nepalese-Tibetan border and taken to a detention facility, where she was held incommunicado for two months. She was interrogated by Chinese intelligence personnel about her employment in Dharamsala. She denied having been politically active and insisted that she had gone to Dharamsala for studies. In response to this, the intelligence officers pulled out a dossier on her activities and presented her with full transcripts of her Internet chats over the years. They indicated that they were fully aware of, and were monitoring, the Drewla outreach initiative and that her colleagues were not welcome to return to Tibet. They then released her and she returned to her village.
 
ASK the participants the following questions:
 
        	● How do you think the authorities could have been monitoring Drewla?
 
        	● What could have prevented this monitoring?
 
        	● Do you know of any other stories like this that you would like to share?
 
Use the example of Using Google Drive to create a threat-vulnerability-capacity model
 
EXPLAIN: Using Google Drive removes the threat of attachments.
 
ASK: Is there any threats associated of using Google Drive? If no answer, ask the question on how much do you trust Google? Would any file that was shared with google drive make you less vigilant?
 
ASK: If you cannot preview and attachment in Google Drive? What would you do? Follow up with questions regarding the use of Dropbox and other software.
 
ACTIVITY: Get the group to come up with a list of software or services they are using. Start working on the risk associated with each software.

ASK: What are the vulnerabilities associated with this software? What can be done to improve your capacity with regards to the threat and vulnerability?

Use the following sheet to fill in the threats, vulnerabilities and capacities based on the above exercise and then have it on the wall for discussion where others can add capacity to mitigate the threats.





|Threat|Vulnerability|Capacity|
|-----|-----------|----------|
|Arrest and confiscation of mobile phone by authorities	|Participating in direct action protest	|Password lock screen Encrypted phone|
| | | |
| | | |
| | | |
| | | |
| | | |
 	 	 
## Section 3 : Malware and targeted malware - problems and solutions ##

DEMONSTRATION:

Malware – Show how a malware works by using a remote login app. We can use TeamViewer/google remote desktop as a software to explain how easy it is to access another computer via a software.

In this exercise we will introduce concepts around targeted attacks

EXPLAIN: Targeted Attacks will result in:	
6.	Compromised 	Accounts 		
7.	Compromised 	Computers	
8.	Compromised 	Mobile Phone

EMPHASIZE: Based on the research most of the attack vectors targeting Tibetans use malware attachments.

 

EXAMPLE 1: The fake Cheng Li.

 

EXPLAIN: 1) Email has been targeted using personal as well as an emotional appeal in order to make the recipient want to open it. 2) Sender is a real person who is distinguished in his field and is very likely to be traveling to China and interested in Tibet research.

DEMONSTRATE: Search for and show Cheng Li’s online profile.

 

EXPLAIN: The attachment has malware attached. However the malware was meant for attacking a computer using the Windows operating system.

EMPHASIZE: These attacks are not always automated. In this case there is an actual person specifically behind this attack. Attackers can also adapt/change their strategy based on your response.

 
And based on the email, this was the reply!

 

EXPLAIN: The malware was changed to work on a Mac computer, but in the end it didn't work. That the attacker tried to change the malware to work on a Mac shows intelligence as well resources behind the attacker i.e. they have the time and capability to correspond with Lhadon and change the malware based on that correspondence.

EXAMPLE 2 - Android APK

EXPLAIN: Even an Android APK file can be repurposed, especially if it was not downloaded from Google play or other verified app stores i.e. shared via email or other means.

 

SHOW: Use the comparison snapshot of the legitimate APK and the malicious APK to show how the app was changed and more permissions were added.
 


Prevention and Detection of Malware

Understanding Headers in email to detect social engineered emails.

What is a header?

Every email message includes a block of text at the top that is referred to as the header. The header contains details about the message, including the sender's information, the recipient's information, the servers that handled the message as it traveled from the sender to the recipient, etc. However, many email clients don't display the header information by default. However there is no option to display headers in a mobile device.


Gmail to display header:


 

 

Thunderbolt


   







Step 1: Before checking headers, one can be a 30 second detective to figure out whether an email should be suspected.

Common Red Flags to be watched out for:

1. Unknown Sender
2. Known sender but different email domains. Example: john@tibet.net vs john@gmail.com
3. Mispelled names with same email domain. Example lobsang@gmail.com vs lobseng@gmail.com
4. Attachments in the email even from trusted senders incase you are not expecting an attachement and in some cases even if you are expecting an attachment. Always beware if an email contains an attachment.

What does a Header look like?

Sample Header:

 




Header training Slides by Jakub Dalek:

https://docs.google.com/a/tibetaction.net/presentation/d/1CpF6tlFF3Nm8y-FDtoSdJtCH6chgclPTOl9v7AJvSX8/edit?usp=sharing

Checking files for problems slides:

https://docs.google.com/a/tibetaction.net/presentation/d/1RbpUqiqX3dhmK4-FdudN_-q1597fC3ugMvG9WFOdzyQ/edit?usp=sharing
  
## Section 4 : Targeted Website Attacks - Problems & Solutions ##

In this exercise we will introduce concepts around how a website is compromised so as to attack the visitors to the site. 

ASK: What is a waterhole attack?

EXPLAIN: This is a method of targeting sites which are likely to be visited by targets of interest. The attacker will compromise the site and inject JavaScript or HTML to redirect victims to additional malicious code or download malware onto the visitors device.

EXAMPLE: An attacker understands that Tibetans will visit a website such as tibet.net or tibettimes.net frequently to access news about Tibet. As such, the attacker will focus on attacking the website itself to reach many people at once, rather than attacking each individual user one by one.
 

EXPLAIN: The attacker understands that he/she will not be able to target everyone, so instead looks at what the majority of people are using in terms of software and operating systems such as Internet Explorer and unpatched Windows or web browsers. As such, he/she understands that the group of people he is targeting are likely to have these vulnerabilities and will visit the website sometime during the period of time when the website is compromised.
 

EXPLAIN: Based on the people being targeted, the attacker then finds a vulnerability/issue with the website and finds a way to compromise a website. After compromising the website, all the attacker needs to do is wait for the targeted people to visit the website. If they have the specific vulnerability/issue that the attacker has exploited, they will become infected just by visiting the website and viewing the infected page. This is a lot less effort than trying to go after each person individually and can result in many more successful infections for a lot less effort!
 





Solutions to checking websites and issues with the website slides

English : https://docs.google.com/presentation/d/1wPQ0eyhKCiZAA-Y7Yo7WnnJodWNyRBGdxMzYLTxxTT8

Tibetan: 
https://docs.google.com/presentation/d/1I0MWjpwZrVRGblPtBsFZ0Z3AUF9rnTnA4eJmR6ZOxrE


  
## Section 5 : Responding to Compromises & Mitigation ##

There is no ultimate security and especially when you work for the Tibet movement or communicate with contacts, there is a chance they you might be compromised at a certain point in time.

Being compromised is nothing to be ashamed about and hidden as even the best security techniques have a flaw which can be compromised. However understanding mitigation and how to respond to compromise is a must keeping in mind that in time you or your contacts might be compromised. 

A few key concepts needed for Responding to Compromise and Mitigation

Encryption:
The translation of data into a secret code. Encryption is the most effective way to achieve data security. To read an encrypted file, you must have access to a secret key or password that enables you to decrypt it. Unencrypted data is called plain text ; encrypted data is referred to as cipher text.
There are two main types of encryption: asymmetric encryption (also called public-key encryption) and symmetric encryption.

Explain how encryption can help even if you are compromised to a certain extent where if the data online or on your computer is encrypted, it would still require the secret key to read the contents.

Explain the concepts of Caesar Cipher or Shift key cipher which is one of the oldest known encryption technology by using the video below:

https://www.youtube.com/watch?v=o6TPx1Co_wg

Symmetric Encryption:

	 	 	
EXPLAIN: Symmetric encryption is basically having a single password to encrypt and decrypt a file. If you have file, you encrypt it using a single key which can then be shared with anyone and only someone who has the key can read it. For the rest, it is encrypted or gibberish. Caesar Cipher is an example of this. (It is more complicated than this, but the basic idea is the same and no need to go into detail as it can get complicated)


Asymmetric Encryption

	 	 	
EXPLAIN: Asymmetric encryption requires the use of a public key and private key. Even though we talk about it like having 2 keys, the way to understand it better is thinking that only you have your private key and unlimited number of locks which you can share with others. When someone locks a message with your lock, since only you have the key, only you can open it. Therefore you can share the lock publicly to anyone who wants to send you a secret message. In the same way, if you have the someone else’s lock, you can send them an encrypted message as well. Though it can be explained in more complex terms but the general idea is the same.


	 	 	
HTTPS encryption: Since we have discussed earlier the concept of https and how important that is, it would be good to explain how that works and without going into the technical part or it, it can be explained in the following way using colors. HTTPS is public key encryption that works between your browser and the server instead of between people.

EXPLAIN HTTPS encryption using the color method using the following YouTube Video: https://www.youtube.com/watch?v=3QnD2c4Xovk


Training manuals: We already have the training manuals for the following in Tibetan and English:

	 	 	
Truecrypt: https://drive.google.com/open?id=0B_BmOs7elgVrT21VNmItMWU1cFE
PGP: https://drive.google.com/open?id=0B_BmOs7elgVrMl9zRldNZnhlQm8
Eraser: https://drive.google.com/open?id=0B_BmOs7elgVrVWYwdkdqbWs2aTA
OTR: https://drive.google.com/open?id=0B_BmOs7elgVrOS1va18xZEFQdzQ

Understanding Censorship and Circumvention

What is Censorship?


The general notion of online censorship is when websites or contents and information is blocked in order to prevent users from seeing them. Censorship is way more protruding than that and can be enforced by different layers of organization and individuals including government, ISPs, Local Area Network at various public internet services (Cybercafe, Library, Hotels and restaurants, etc.). It is the suppression of users ability to access, view or publish online. It also refers to when individuals resort to self-censorship through intimidation.
 
Censorship is a phenomenon that takes place in different forms and may vary from nation to nation, or even among regions within a nation.

There are numerous tactics used around the world in order to enforce Censorship.

Top-down Censorship
9.	Shutting down Internet
-	Blocking websites deemed as threat to stability of the nation in order to preventing users from accessing websites .
-	Filtering contents (from website, forums, search engines, chats, etc.),
-	Distributed Denial of Service attack by targeting popular opposition websites by attacking their web traffic making it impossible for users to visit the site.
-	Intimidation tactics like Imprisoning and Torturing bloggers and dissidents and create general fear amongst public from posting opinions against the authority.
-	Manipulating unfavorable online content (mostly articles) by bombarding the comment section in attempt to change the direction of the conversation.
-	Raising cost of internet subscription making it inaccessible for general population.
-	Crippling the network so that connection to an application or website becomes so slow that it is unusable.

Bottom-up Censorship

-	Self-censorship happens from groups or individuals out of fear of retaliation.

The tactics mentioned above are the more general tactics of censorship.

What is Surveillance?

Surveillance can happen at different platforms - from monitoring street activities in the area we live in with  CCTV, to monitoring our online activities. Unlike online censorship where you experience websites being blocked or contents taken down etc., internet surveillance is something that takes place underneath the network and is not visible to the users. But, both Censorship and Surveillance go hand in hand. 

Authorities use sophisticating internet and wireless technology to censor, monitor, collect and retain communication data. Many governments and law enforcement agencies monitor online communication including location of individuals and groups.

> The reach of these technologies is astonishingly broad: governments can listen in on cell phone calls, use voice recognition to scan mobile networks, read emails and text messages, censor web pages, track a citizen’s every movement using GPS, and can even change email contents while en route to a recipient. Some tools are installed using the same type of malicious malware and spyware used by online criminals to steal credit card and banking information. They can secretly turn on webcams built into personal laptops and microphones in cell phones not being used. And all of this information is filtered and organized on such a massive scale that it can be used to spy on every person in an entire country.
> > Electronic Frontier Foundation (EFF)
		
		
> (EFF is a well known international non-profit digital rights group.)



Since governments have complete access to the network traffic, they can easily see the contents of data if not encrypted. 

Circumvention: how to stay anonymous online.

Unless the rule of law is in place, authoritarian regimes will continue to censor and monitor all forces of change including citizens who may not agree with government policies or leaders and are deemed as threat to the regime. 

There is no absolute solution to stop censorship and surveillance but there are means to avoid them. 

Technologies like Proxy servers and VPNs allow us to bypass both censorship and surveillance.

Here are some examples of the good circumvention tools that are out there for use, free of cost.


Psiphon: android, windows
https://psiphon.ca/en/download.html

Free Browser - Android 

http://openitp.org/org.greatfire.freebrowser.apk
https://play.google.com/store/apps/details?id=org.greatfire.freebrowser&hl=en

Tor - windows, Mac, Linux
https://www.torproject.org/

Orbot - VPN or a browser - Android based
https://guardianproject.info/apps/orbot/




Advanced Topics here:

Using Network Monitors/firewalls:  Glasswire for windows, Little Snitch for Mac.
Using Sysinternals for windows
Using Wireshark

  
	 	 	

## Section 6 : Phone Security - Basic Mobile Security & App Security ##

EXERCISE: Risk Race (5-10 mins) - start this section immediately with this exercise, before talking at all about mobile security.

Stand at the back of the room in a line. Goal is to get to the opposite end of the room first.
- step forward 2 steps if you have a mobile phone
- step forward if you signed up for your SIM card with your name
- step forward 2 steps if you carry it with you everywhere you go
- step forward 3 steps if it is with you 8 hours or more a day
- step forward if you use SMS on your phone
- step forward 3 steps if you store all your contacts in your phone
- step forward if you use email on your phone
- step forward if you have photos on your phone
- step forward if you use facebook on your phone
- step forward if you have WeChat on your phone
- step forward if you do any financial activities on your phone

ASK all the participants to say what they thought this exercise was about. Why do you think someone is at the front and why someone is at the back of the room?

Start a discussion on what are the benefits and risks of using smartphones? Illustrate the difference between a mobile phone and smartphone where a mobile is a communication device used for calling and texting only, whereas a smartphone is not only a communication device, but also a mobile computing device (essentially a computer in your pocket) which has all the functionalities of a mobile phone as well.

1. Basic Mobile Security

SHOW: Tibet Action Mobile Security Video # 1 - Your SIM card and your mobile phone can identify you


IMSI - International Mobile Subscriber Identifier
IMEI - International Mobile Equipment Identifier

EXPLAIN: The difference between an IMSI number and IMEI number is that the IMSI is in the Sim card which you purchase from your telecom provider and IMEI is the number is in your mobile device itself/connected to the actual phone hardware.

EXPLAIN: Your phone IMEI number is linked with the IMSI number once the two are connected and used to make a call. They are registered and now linked together.

TASK: Use the example of a Tibetan inside Tibet calling someone outside Tibet to share some news? What would be the safest way to make that call based on the above understanding of IMSI and IMEI if he or she didn’t want to be traced or identified?

Try to get the participants to work together to answer the above question and what would the ideal situation be in this case and ask them to come up with a plan.

Task Solution: The individual in Tibet would use 2 different sim cards and 2 phones which are never connected to each other and also making sure the Sim card used to call India is not registered to the individual directly. Also at the same time, the person in India who they are calling needs to have a phone number which is not known to the authorities inside Tibet as they might be monitoring outgoing calls to a particular number.

SHOW: Tibet Action Mobile Security Video #2 - You Mobile Phone Can Track You

ILLUSTRATE: Create a diagram as illustrated in our flyers to show triangulation via cellular towers.

ASK: How do you receive a call? Answering this question will allow the trainer to explain the fact that a phone is always connected to a cellular tower if available and always communicating, even if you are not using it actively. This is how mobile phones work.

TASK: Use the example of a Tibetan inside Tibet calling someone outside Tibet to share some news? Now understanding that phones can be tracked, what would your advice be to the person in Tibet.

Solution should include: Having a separate phone and sim is a must. Also this phone must be switched off and battery removed at all times and should only be used to call from a location which is not his own place. Also, the two phone should never be switched on at the same time because then they will connect to and register on the same cell tower and can later be linked together by the authorities.

EXAMPLE: Your phone can track you

SFT/Hu Jintao protest - SFT action in Delhi. Wherever SFT Dorjee Tseten was, he was being followed. SFT members in MT knew the area would be watched so they went to friend’s place in south Delhi. Tselha and Tensonam were chatting through Kakao. DT’s location was traced via his cell phone (his usual number) and police actually came to the area in south Delhi with his photo and started asking where he was from door to door. Dotseten left in a hurry and police came around 2am to exactly the location where he had been staying and took his friend away.

EXAMPLE:Your phone can identify you

TYC recent action - Foreign Minister of China came and TYC members were all in MT. All towers were blocked so cell networks weren’t available. They used Wifi instead. Jigme couldn’t contact media as his phone number was blocked as such any media trying to contact him was unable to do so.

EXAMPLE: Your phone can track you retroactively

Tselha in Pune - Tselha was in Pune and there was a bomb explosion in the German Bakery. She and her friend were in a cafe next door. They’d heard there was a Bollywood star coming by so they went there and then they left and found out later about the xplosion. Police called her 2 days later and told her to come to the station and asked what she was doing there and what she was studying etc.

EXAMPLE: Your phone can listen you

Reporter Story - Beijing reporter out with officials when one took him into the next room and, showing off, demonstrated that they could listen in on the conversation in the next through his phone. *This story can be used to illustrate the fact that a phone which is always with you is like having a microphone with you at all times. It can be used to listen to you as long as whoever wants to listen to you has access to the telecom provider. Even if they might not have telco cooperation, it can also be done if there is a backdoor on the phone itself or if the phone has been infected with Malware.

QUESTION: Would you use your phone or keep it with you during an important meeting? Asking this question highlights the fact that keeping the phone with the battery removed or in a separate room should be in any operational security protocol if you don’t want to be listened to. Also add the fact even putting a phone inside a bag is better than leaving it sitting on a table. Putting a phone is airplane mode can help but there is no guarantee that there is no signal in this mode.


2. Smartphone Security


SHOW: Tibet Action Mobile Security Video - Think Twice before using WeChat

Using WeChat to understand permissions in application on smartphones. (In Tibetan)

Chatting live with friends is fun! Discussing issues we care about in a group is fun! Connecting with our near and dear ones is even more fun! But, as fun as it has become connecting, with thousands of fancy mobile apps available for free to download, we have now opened our lives not only to people we are connected with, but also to individuals, companies and governments handling the layers of network to connect to the app server. One of the major apps that has access to our communication, location and contacts is WeChat (Weixin) of Tencent, a Shanghai based company.


There are several things that we’ll cover here regarding communication apps in general and some more specifically about WeChat, its merits and demerits from the point of view of a Tibetan user, what to look for when we install such apps. 

10.	Don’t install if you don’t need them 

Installing all the apps we find cool may take up space on our phone and slow down our phone. Only install the ones we need in our day to day life. This will make our lives less complicated and our data more secure.

11.	Always read the app permission before installing

Do you ever read the app permission before installing an app on your phone? If no, you are not the only one. Most people do not read, hence are not aware of what the app could do on our phone.

Let’s say, would we allow any stranger we meet on the street into our home? And if we do, would we let that person wander freely in our house, picking up our belongings? No, right! Similarly, we cannot allow an app we don’t know into our digital lives before finding out what the app could do on our phone beside its functions.

Majority of the apps we find in the app store/play store are permission hungry and many access our personal data that are not even needed for the functioning of the apps. Question ourselves if such permission makes sense. Eg., if we are installing a Clock, if the app asks to access our call record, contacts, messages, gallery, etc., ask ourselves if a clock really needs to access all these data on our phone. If not, then look for other options available.

Let’s go through some of the permissions that we have given WeChat when (if) we installed the app on our phone.

WeChat will have access to:

 
WeChat will know what other apps are running on our phone.
 
WeChat will know what other accounts we have registered on our phone and has the ability to remove or add accounts
 
It can read all our contact information and modify them
 
WeChat knows where exactly or approximately we are.
 
WeChat can access and read our regular text message or MMS.
 
WeChat can access contents of our USB storage or SD cards and has the ability to modify or delete files in them.
 
WeChat can access our phone status, our call logs including who we have been contacting through our regular phone.
The above are some of the permissions that we have given WeChat while installing it.

We must also understand that almost all apps, especially communication and social networking apps have similar invasive features as WeChat. If that’s the case, then how do we weigh similar apps before choosing the right one?
Beside assessing what the app could do on our phone, it is really necessary to take into consideration few other things that are as important.
12.	Encryption

In an ideal situation, the most private way to send a message is by using an app that provides end-to-end (peer-to-peer) encryption. This is when only you and your friend can see the encrypted conversation after exchanging keys and verifying one another. In this case, encryption happens between the sender and the recipient and no one else in the middle (from the layers of internet network) can see the content. 

If not end-to-end encryption, at least find out if the app provides encryption in transit between you and the server. Most chat apps have adopted this form of encryption, but it doesn’t hurt to double check.
For example, WhatsApp has end - to - end encryption but having end to end encryption alone is not enough, we also need to understand how that has been implemented and whether it has known security flaws in its implementation.


13.	Who owns this app
The first thing we must do is to find out who runs the app. Depending on where we live in this world, we must look at if the company or that individual running the app has any voluntary or forced obligation towards certain government we may want to avoid. Also find out if they have any history of handing over user data to any government who have requested for it, esp of those who are involved in social or political activism.

14.	Server Location

	On top of finding out who is running the app, we must also find out where the app’s server - where all our data is stored - is based in. In the case of WeChat, its server is based in China and any company or institution running/registered in China have the legal obligation to obey government orders in matters of state security." Correlated to point # 4, apps that are not based in China can also share Data if the app is registered in China. Whether this will happen or not is uncertain but companies registered in China are required to turn over user data under the Chinese law. One case in point is the Line, a Japanese based app, also called Lianwo in China is registered as a company in China. Studies by independent researchers indicates that the app is allowing law enforcement to eavesdrop on communication. Studies have also shown that the app is actively implementing keyword censorship for users in China.

Many of us believe that if we are not involved ourselves in sensitive efforts, then our conversation doesn’t really hold any importance to anyone. This is not true.
By looking at what the app could do on our phone, including getting access to our contacts, even if they are not interested in us, they might be interested in someone in our contact list, or their contacts
And if we are politically or socially active, then we can be monitored and may even put our contacts who are not active at risk for merely knowing us.

APPS to install and show how to use:
Zom -  https://zom.im/
Orbot - https://guardianproject.info/apps/orbot/



[visit Melhong](http://melhong.com)


[Leave a Message forms ](https://dawapaljor.github.io/testmd/form.html)
