# Department of Defense Cyber Sentinel Challenge
![DoD Cyber Challenge](https://github.com/mpmatusek/DoDCyberSentinelChallenge/assets/167713753/6cbfa0d1-ef10-4f75-b10b-198628f852bb)

The Department of Defense sponsored a recent CTF (Capture the Flag) event that attracted 5000 applicants in May 2024. For those of you who don't know, a CTF event is one in which participants compete for a cash prize and bragging rights to be in the top ranks of upcoming and current cybersecurity professionals. The challenges ranged from easy to hard among several cybersecurity categories; this year the featured categories were Web Security, Malware/Reverse Engineering, Forensics, OSINT (Open Source Intelligence), and Networking/Recon. 

<h2>My Experience</h2>

Althought I had never participated in one of these challenges before, I was certain that I'd be able to complete at least some of the easy ones in a variety of the categories. I was happy enough to walk away with the rank of 638th out of 5000 participants and the knowledge of completing at least three of the easy challenges and coming close to getting three others. The three challenges I was able to complete and earn points for included the "Printer", "Ephemeral", and "Have you Bean here before?" challenges. I will highlight my own strategy in completing these and then I will spend some time discussing how I approached the challenges I nearly completed which included the "File Issue", and "Targeting" challenges.

I spent a fair amount of time at the beginning making sure all of my tools in Kali Linux were operating as expected before the challenge started; some of the tools I had never used prior to the experience, and others I had just recently learned about utilizing the TryHackMe lessons. Suffice it to say I was a bit overwhelmed when the challenge started, but I pressed forward and did the best that I could given the resources and time available. Not since my time as a graduate student in physics had I been challenged so thoroughly like I was during this event, and maybe I am a bit sadistic in this regard, but it felt good to feel that challenge once again!

<h2>Challenge 1: Printer</h2>

This challenge involved a ticket where an end-user needed access to the control panel of a printer hosted on a server.  The end-user had forgotten their password and requested our help to retrieve it. The web app hosted at https://web-printer-t34jla4lcq-uc.a.run.app redirected users to a login page and it was our task to discover and login to the app. Initially, I considered using a brute force method to crack the password. I tried several common usernames like "Admin", "Admins", and "admin" with various passwords from a wordlist I found through a quick Google search [Word List](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/10-million-password-list-top-1000000.txt).

Despite these efforts, I realized brute force was too obvious and time-consuming, prompting me to explore alternative methods. Consulting AI about common password issues on web pages reminded me of the robots.txt file, which can sometimes expose sensitive directories. I navigated to the robots.txt file of the web application and discovered it listed a notes.txt directory. Accessing this directory revealed the administrator password. Using this password, I gained access to the control panel and successfully completed the task, marking the discovery of my first flag.

<h2>Challenge 2: Ephemeral</h2>

This one was pretty clear to me. I don't remember all the technical details, suffice it to say an attacker was using ephemeral ports to do some dirty business to the victim in question. The first part of this challenge required the ephemeral port discovery which was easily done (but time consuming) using nmap -Pn -p- -T4 34.31.144.172 which revealed the ephemeral port 51147. I then ran a simple curl 34.31.144.172 51147 which immediately gave the required flag. Fin.

<h2>Challenge 3: Have you Bean here before?</h2>

This challenge presented a photo that a threat actor took at a restaurant somewhere. Using open-source intelligence it was our task to identify where the threat actor was located based on the image shown below.

![photo](https://github.com/mpmatusek/DoDCyberSentinelChallenge/assets/167713753/5ffe5c3d-007f-47b2-b9e6-7e9ae8edddf5)

I probably jumped the gun on this and immediately thought "look at the metadata for gps!" what again, was far too simple. I ran exiftool on the image revealing all the good metadata we expect with all the location related data stripped away. So then I decided that a more creative solution would be required using actual open-source intelligence. So my first move was to look at the image a little closer, revealing the name "Paul" on the mug. Then, upon noticing common structures uniquely tied to locations in the United States (i.e. crosswalks, traffic lights, signs, etc) I decided that wherever the culprit was must be within the states somewhere.

Having spent time in Europe I immediately identified the food on the table as European and that the drink looked somewhat like a coffee. So I queried Google for Paul's Cafe which immediately gave me three different locations, all within the proximity of Washington D.C. I next used Google Maps to compare the photo to the street view of each location, pinpointing the exact address as 1275 K St NW, Washington D.C.

![image](https://github.com/mpmatusek/DoDCyberSentinelChallenge/assets/167713753/39ee6589-d0ac-4085-b330-a45a7e5a8586)


