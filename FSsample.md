Functional Specification: X-Day Calculator
==========================================

NOTE: This is a sample functional specification for the HHS Programming in Action Course. This is not 
an attempt to specify an **actual product**.

Introduction
------------

The **X-Day Calculator** is a web-based application that will allow students to estimate the probability
of "getting an x" in a particular class. 

This specification does not attempt to define either the methods used to estimate probability of "getting
an x" or the underlying web technology that is used to implement the service.

Site Design: General Principles
-------------------------------

This web application will ultimately be found at the domain name: http://xdaycalculator.net (nothing
there right now!).

All pages in this site will render appropriately for desktop and mobile devices. They should not 
require the user to scroll in order to interact with the site. This is an example of "responsive web design" 
(look it up).

Pages that render for desktop/tablet use will prominantly display the site name:

>  X-Day Calculator
  
and a site logo in the upper left hand corner:

![alt text](https://github.com/HHS-Programming-in-Action/documents/blob/master/xcalclogo.png?raw=true)

Rendering for very small devices (phones) may omit the logo and site name, if necessary to fit everything 
in to a single non-scrolling screen.

Home Page
---------

The main landing page includes the following form elements:


| **Label**                | **User selection**                                              |
|--------------------------|-----------------------------------------------------------------|
| Department               | n/a, math, science, english, social studies, art, PE (pulldown) |
| Teacher                  | n/a, and a list of names (pulldown)                             |
| Days since last X        | text box for numeric entry                                      |
| Days since last snow day | text box for numeric entry                                      |

The page should also have the following hyperlinks:

* About
* Terms of Service
* Contact

