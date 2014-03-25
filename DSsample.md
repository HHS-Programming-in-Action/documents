Design Specification: X-Day Calculator
======================================

NOTE: This is a sample design specification for the HHS Programming in Action 
Course. This is not an attempt to specify an **actual product**.

Where the functional specification attempts to describe a "black box" from 
the **outside**, the design specification describes it from the **inside**. 
An ideal design specification would be a full description of how a system is 
designed, such that a competent engineer could read the specification and 
build the system so that it works as specified.

Introduction
============

The **X-Day Calculator** is a web-based application that will allow students 
to estimate the probability of "getting an x" in a particular class at Hanover 
High School. Please refer to the Functional Specification document for details 
on operation and behavior.

This design specification will provide details on the following architectural 
elements of the product:

* Server software and overall architecture.
* Server side programming language.
* Client side programming language.
* Data storage requirements and tool choices.
* Server system architecture 
* Client system architecture
* Major entry points (URLS) to the site.
* Mathematical model for determining X-Day probability.
* Software test strategy.
* Bug tracking strategy.
* Software deployment instructions.

Server Side Software and Architecture
=====================================

The X-Day Calculator will use the current released version of the Open Source
Apache web server, running on a virtualized PC running on a the latest LTS 
(Long Term Support) version of the Ubuntu Gnu/Linux operating system, in 
"headless" mode (no GUI). The choice of virtualized PC vendor is beyond the 
scope of this specification.

Server Side Programming Language
================================

The X-Day Calculator will use server-side scripting in the form of Python, 
running within the Flask web application framework. 

Client Side Programming Language
================================

Any client side scripting will be written in Javascript, with the support
of the Twitter/Bootstrap javascript library.

Data Storage Requirements and Tool Choices
==========================================

A persistent data store on the server will be maintained using a SQLite 
database via Flask APIs. The SQLite data store will be a file stored in 
the same server directory as the Python sources. The database will be
accessed by writing appropriate SQL commands.

Database Tables
===============

The following tables are planned for the X-Day Calculator data store:

departments
-----------
Fields: id, departmentname

Notes: this table serves to keep track of all departments in the school.
Other tables will reference departments by id.

teachers
--------
Fields: id, teacherlastname

Notes: this table serves to keep track fo all teachers in teh school.
Other tables will reference teachers by id. There is no need or effort
to associate teachers with departments, although this may be a good
candidate for feature expansion in the future.

departmenthistory
-----------------
Fields: departmentid, dayssincex

Notes: every visitor to the site will report the relevant department and 
the number of days since the last x-day. Each visitor report will cause 
a new record to be added to this table. 

teacherhistory
--------------
Fields : teacherid, dayssincex

Notes; every visitor to the site will report the relevant teacher and
the number of days since their last x-day. Each visitor report will cause
a new record to be added to this table.

Server System Architecture
==========================

Server is implemented using WSGI interface to Python via the Flask framework.
Visitors to the home page will have the option of filling in a simple form
in which they report a teacher and department and the number of  days since
the last X-Day. The server will accept this information and use it to add
records in the departmenthistory and teacherhistory tables in the SQLite 
database.

The collection of these visitor-reported so-called facts about teacher
and department behavior are used to generate a predicted probability of
an X-Day, based on historical behavior and the number of days since the last
snow day. Consequently, upon submitting the form, the visitor will be 
redirected to a page that displays the forecast X-Day probability.

To ensure stability of the server software versions, a virtualenv will be
established with the current latest versions of Python and the Flask 
framework. The Apache server configuration will have to be modified to ensure
the virtualenv context is used when executing Python code in Flask.

Visitors are not required to log in and no user information is retained
on the server. A session variable is created in Flask for each visitor, 
whih is used to keep track of user state (e.g. is the visitor supposed
to be viewing the prediction result or the prediction request form).

All user input shall be "sanitized" prior to including it in SQL 
commands.

Client System Architecture
==========================

On the web browser side, Javascript will be used to deliver a modern, hip web
browsing experience. Dynamic UI elements will used with wild abandon with the
assistance of Jquery and Bootstrap Javascript libraries.  Layout of the page 
will be responsive to client device (phone through desktop) by making use
of the built-in functionality of the Boostrap library.

Web page design will use HTML and CSS effectively, with HTML reserved solely
for content and CSS for style, layout and background images. When practical
to do so, CSS may be used for dynamic UI elements, otherwise Jquery/Bootstrap
should be used

Major Entry Points
==================

/
~

The root page for the X-Day calculator, including a form for fequesting an X-Day
prediction. The resulting page will be served at this URL as well. This entry point 
will be served by Python running in Flask.

The following entry points are written as static templates, served via Python/Flask. 
This will enable the entry points to be updated with server-side dynamic content 
at a futture date.

/about
------

Self explanatory.

/tos
----

Terms of service.

/contact
--------

Contact information for the site owner.

Mathematical Model
==================

Probability of an X-Day is calculated by considering the average number of days since
an X-Day in the chosen department (N<sub>d</sub>) and the chosen teacher (N<sub>t</sub>). 

Probability, without regard to recent snow day activity, is calculated thus: 
P<sub>raw</sub> = 100% x (1/N<sub>d</sub> + 1/N<sub>t</sub>)/2

A "Snow Day Multiplier" is applied to P<sub>raw</sub>, with the effect of decreasing
X-Day probability when a snow day has been called within the last five days. If the
number of days since a snow-day is given by the variable, N<sub>s</sub> then:

  Praw = 100.0 * (1/Nd + 1/Nt)/2
  if Ns < 6:
    P = Praw / 5   # X-Day probability is very low
  else:
    P = Praw       # Ages since a snow day, probability is unaltered.
    
This model is developed based 100% on my hunch for how it should work. I think I'm right.

Software Test Strategy
======================

Software testing must be used to ensure both server and client-side programming
are bug-free. No code shall be deployed to the server unless all automated and 
manual testing on the new version is completed with 100% success.

On the server side, the built-in facility for unit testing in Flask will be used.

On the client side, a human will execute a series of predetermined test cases, noting
deviations from expected behavior in a log:

Test cases shall include "normal" input sequences as well as "bogus" sequences.
Examples of bogus inputs include:

* Entering non-numeric data in a numeric field (e.g. "this sucks" instead of "5" 
  for the number of days since the last X-Day).
* Entering invalid numeric data in a numeric field (e.g. "-5" instead of "5"
  for the number of days since the last X-Day).

In every case, entering invalid data on the web browser will prevent the submit 
takng place, and no result will be displayed.

Bug Tracking Strategy
=====================

Source code will be archived/maintained under a Github account. Users and testers 
may submit comments on code through the Github feedback facility. I don't know
exactly how this works yet, but I think it will be fine.

Software Deployment Instructions
================================

