--- 
layout: post 
title:  First cBioPortal Hackathon
tags:
- cbioportal
- hackathon
---

<div class="photo-right">
	<a href="https://raw.github.com/ecerami/ecerami.github.io/master/img/hackathon2.png"><img src="https://raw.github.com/ecerami/ecerami.github.io/master/img/hackathon2.png"></a>
	<p>cBioPortal hackers hard at work.</p>
</div>


On December 7 and 8, we organized our first ever <a href="http://www.cbioportal.org/">cBioPortal</a> Hackathon.  For those unfamiliar with cBioPortal, it's a web-based platform for analyzing and visualizing large-scale cancer genomic data sets.  Earlier this year, cBioPortal went <a href="https://github.com/cBioPortal/">fully open source</a>, and we now have a cross-institutional team from <a href="http://www.dana-farber.org/">DFCI</a>, <a href="https://www.mskcc.org/">MSKCC</a>, <a href="http://www.uhn.ca/PrincessMargaret">Princess Margaret Cancer Centre</a>, and <a href="http://thehyve.nl/">The Hyve</a> working on the continued development of the portal.


The Hackathon was hosted at DFCI in Boston.  All told, they were 15 of us, broken out into four teams.

<div class="photo-left">
	<a href="https://raw.github.com/ecerami/ecerami.github.io/master/img/hackathon1.png"><img src="https://raw.github.com/ecerami/ecerami.github.io/master/img/hackathon1.png"></a>
	<p>Pieter Lukasse from The Hyve and Adam Abeshouse from MSKCC presenting performance improvements to the cBioPortal.</p>
</div>

**Team 1:  Data Validation and Importing.**  Tasked with improving the validation and loading of new data sets into the cBioPortal.  Succeeded in extending the existing validator, adding an HTML report option, and made good progress to an overall single script for validating / importing new data sets.

**Team 2:  Performance.**  Tasked with identifying performance bottlenecks in the current code, and working their way through these bottlenecks.  Succeeded in identifying and fixing a number of front-end performance bottlenecks.

**Team 3:  Virtual Cohort Front-End. ** Tasked with building a new "virtual cohort" feature for selecting samples across multiple cancer studies or across multiple cancer types.  Succeeded in defining <a href="https://docs.google.com/document/d/1UNUii4WCpcMxNsu6CA6uJIGq1xcY7sHWorzVt2MJ38I/edit">RFC 16</a>, and building first prototype of functionality.

**Team 4:  Web API and Scalable Data Store.**  Tasked with building the next generation of the web API for cBioPortal, and scaling to accommodate the expected rapid future growth of data sets.  Succeeded in building a first version of cBioEngine, a new MongoDB backed web API.

I think we learned a lot from our first hackathon.  I share these for others contemplating hackathons of their own.

* **Keep the teams small:**  we capped all our teams at 3-4 people.  We reasoned that small teams could make real progress.

* **Pre-Hackathon meetings: ** we tried to defined the teams and priorities ahead of time. Each team was also tasked with meeting 2-3 times before the actual hackathon, so they could hit the ground running.

* **One big room:**  On the first day, we were split out into four separate team rooms.  This seemed to prevent informal communication between the teams.  On the second day, we therefore moved to one large conference room.  The energy and buzz definitely went up.

* **Shared results at the end:**  we reserved the last 1.5 hours of the hackathon for each team to report back and show code.  This was definitely the highlight.

I think the hackathon was a huge success, and we are planning our next one in late February, to be hosted by MSKCC.

