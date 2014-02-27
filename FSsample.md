Functional Specification: X-Day Calculator
==========================================

NOTE: This is a sample functional specification for the HHS Programming in Action Course. This is not 
an attempt to specify an **actual product**.

The software functional specification is an attempt to describe the system as a black box, where all possible
inputs are described, and the corresponding outputs. What this will look like depends on the type of application.

For embedded applications, such as the firmware that runs a fire alarm system, the functional specification would
describe the control panel for the system, the various commands that an operator might make on that panel, 
and the resulting behavior of the system.

For example, "If the operator presses the **test** button, the fire alarm will emit an alarm tone for 5 seconds."

A functional specification may also describe the behavior of the system from the point of view of *other software
systems*. For example, "If a message with this information is sent to the device, it will respond by emitting
an alarn tone for 5 seconds."


Introduction
------------

The **X-Day Calculator** is a web-based application that will allow students to estimate the probability
of "getting an x" in a particular class at Hanover High School.

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

![logo consisting of a large x with a question mark superimposed](https://github.com/HHS-Programming-in-Action/documents/blob/master/xcalclogo.png?raw=true)

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
| Submit                   | (button)                                                        |

The page should also have the following hyperlinks:

* About
* Terms of Service
* Contact
* 

###Submit Action

When the visitor presses the Submit buton, they should be sento the Results Page:

Results Page
------------

The Results Page displays the result of the X-Day prediction, as a single two-digit number with a percent
symbol. For example:

> 36%

This result will be displayed with a blue sans-serif font, on a white background. The font will be as large
as possible while still fitting entirely on the screen, leaving room for the home link (below).

There will be a link at the bottom of this page that returns the user **home**. The **home** link will return visitor to the Home Page (above).

About Page
----------

This page will include the site title and logo (as on the home page) if the browser screen size permits,
and a short, one-paragraph description of what this site is for.

There will also be a paragraph with disclaimer stating that this site is intended for educational and entertainment
purposes *only*.

At the bottom, there will be a one line copyright statement.

At the bottom, there will be a single link for returning to the Home Page.

Terms of Service Page
---------------------

"Use of this site implies acceptance of the following..." Insert legal boiler-plate from the team
of lawyers employed by the Dresden School District for exactly this reason.

At the bottom, there will be a single link for returning to the Home Page.

Contact Page
------------

Something like:

> This application was created by \<name> [as an e-mail link]. 

At the bottom, there will be a single link for returning to the Home Page.
