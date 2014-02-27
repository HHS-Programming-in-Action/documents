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


