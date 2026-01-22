---
layout: post
title: Discipline Form
date: 2020-04-08 06:45
author: k3ntuckyblog
comments: true
categories: [Chrome, CSS, Discipline Form, HR Form, HTML, HTML Design, Javascript, Projects, Stand-alone web form, Web Development]
---

**-OR-Snitches get stitches in the britches...

     HR approached me, like the beginning of so many 'headache' stories, requesting to make a standardized form for reporting disciplinary issues.  Now, I'm no snitch, I try to avoid stitches when possible.  But I do like making processes more efficient.   

      The HR person who brought the idea up stated that a previous job had a word document that acted as the form.  Let's not get it twisted, we could do that... But that would mean diving into visual basic programming.

     From MY previous last job, I made an excel macro that would send out emails reminding people to update their documents.  It was fun enough, I suppose, but learned quickly that VB and I don't get along.

Instead, I decided to leverage my web developments skills and make a standalone web form. 

Let's look at the user story:     Ability to enter the info info of the manager, employee, incident, what actions were taken.     Display the actual wording from the company manual.     Have the form remind everyone what the next course of action would be depending on the actions / issue on the form.     Be able to email / print form as a PDF.

 This is the final product:

**["https://codepen.io/melvinhicklin/pen/ExaJzMV">CodePen.io</a>

Basic looking? Yes.  But we don't need fancy, we just need functional, Fancy can always come later.  

**Of course, feel free to use this form and change it around to fit your purpose.  You can put lipstick on this pig and sent it to the rodeo in your version.  

     Overall, It's a simple form but there are a few things I want to want to point out.  Our current environment uses Chrome as an alternative browser, So a chrome shortcut that would pull up the page directly from a place on our network:"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" file:///<File location>    This gives me the added benefits of native PDF printing along with being able update in the background and users not noticing.Starting at the top we have:

<ul><li>Date and time stamp<ul><li>Simple JavaScript, but I discuss it below.</li></ul></li><li>Drop down menus for the department affected</li><li>Text fields for Associate and Manager names</li><li>Drop down menus for prior and current warnings<ul><li>Selecting Prior auto-fills the current warnings.  Discussed below.</li></ul></li><li>Drop down menu for policy the was violated<ul><li>Fills in an area to show policy  </li></ul></li><li>Button to reset policies<ul><li>I'll discuss that in a bit</li></ul></li><li>Text field to describe how the policy was broken</li><li>Area for the policy selected before is displayed</li><li>Drop down menu for next course of action</li><li>Signature area</li><li>Check and Print button<ul><li>Discussed below </li></ul></li></ul>

The form is simple but I wanted to draw back the curtain and show some of the mechanics behind it:

**Date and Time Stamp**A DIV element, ID of 'dateF' short for 'date field', will hold the date:** var d = new Date();**We take that variable and replace the inner HTML of the DIV element to the string "Date and Time" and concatenate the 'd' variable, here translated into a string with the .toLocaleString method, to the end.**document.getElementById("dateS").innerHTML = "Date and Time: "+d.toLocaleString();**

**Autofill Prior and current warnings**Streamlining the process is a major priority when I make a project.  For me that means automating the redundant, the boring and the annoying little stuff.  Nothing sucks more then having someone introduce a new thing to do resulting in more paper work to do and more boxes to check.  To that end, Making the form as easy as possible means the end users will be willing to accept into their work flow.**f****unction autoFillCurrentWarning(priorWarning) {     var warningToInterger = parseInt(priorWarning, 10);**//**    var nextStep = warningToInterger + 1;**//This is where the 'magic' starts.  The var priorWarning represents what is selected in the Prior Warning field.  Because it comes into autoFillCurrentWarning as a string, we have to use parseInt (Syntax: parseInt(Varible Name, Radix) Radix is the numerical system to use 2 = binary, 10 = demical) turning the string into an integer where we can increament it by 1.  Note: 'i++' could have been used, but I didn't feel like it. ******    var curWarning = document.getElementById("currentWarnSelection");          curWarning.value = nextStep.toString();**//This part takes the integer, places it inside a variable and turns it back into a string.  Once there, it completes the autofill function.  However, inside the form I have a couple of date fields that are suppose to show up if certain warning types come up.  To make sure those fire off, I added an IF statement:**               if (nextStep >= 3) {                    suspend(nextStep);                }**//This calls the 'suspend' function and ensures the date fields display.**}**

**Drop down menu for policy the was violated**The request to have the company policy appear when it's selected from the drop down menu could be better much more efficiently but for this form I ended up using a quick method.  The DIVs holding the policies are hidden with CSS: display:none;When a policy is selected from the dropdown, the onChange passes what was selected:**select id="polVioC" class="drop" onchange="polVioSelect(this.value)"**

The JS function polVioSelect adjusts the CSS based on the DIVs id:**function polVioSelect(polVioChoice) {     var pick = polVioChoice.toString();          if (pick == "safe" || "unac" || "time1" ||"time2" || "unsat" || "other" || "hara" || "sex") **//I know there is a better way to set this up, but this was the best solution I could come up with.  If I find a better way to refactor, I would like to revisit it.**{               document.getElementById(polVioChoice).style.display = "block";          }}**

**Button to reset policies**So, due to a lack of knowing everything, I ended up making a button to clear out the policy area.  The button adjusts the CSS back to display:none for all the DIVs that have display:block.  It can act a little weird every once in a while but it gets the job done. 

**Notes about @media**The buttons are part of a CSS group that turns them to display none while printing:**@media print{     print{          display:none;     }     reset{          display:none;     }}**@media allows you to make special CSS groups for different screen types.  You may want your page to display different on a tablet verses a cellphone verses a desktop.  Here we are saying 'When we print this page, the buttons will not be displayed'.

**Submit button**Normally the submit button is attached to a PHP action and will run validation checks before giving it to the server.  For this, I added a 'Check and Print' button and made a simple Javascript function for the button to call.  If everything is filled in, the print window pops up.  If something is missing, a pop up notifies the user that a field needs attention.  First we add a .onsubmit event listener to call our Javascript function (checkAndSubmit):**document.getElementById("discipline").onsubmit = function() { checkAndSubmit(); };**Then our actual function goes off:**function checkAndSubmit() {event.preventDefault();**//This prevents the default function of 'submitting and resetting' the form.**window.print();**//This is the actual print function called.**return false**;//No info is being returned, so we set this to false.**}**

**What did we learn / TL;DR**Made a HTML 5 Discipline form.  Names have been changed to protect the innocent.  Learned a couple neat tricks: Auto-filling drop down menus.Having HTML form checking with JavaScript.Making Buttons disappear when printing.

