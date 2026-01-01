---
layout: post
title: Discipline Form
date: 2020-04-08 06:45
author: k3ntuckyblog
comments: true
categories: [Chrome, CSS, Discipline Form, HR Form, HTML, HTML Design, Javascript, Projects, Stand-alone web form, Web Development]
---

<p class="has-text-align-center">-OR-<br>Snitches get stitches in the britches...<br></p>

<p>     HR approached me, like the beginning of so many 'headache' stories, requesting to make a standardized form for reporting disciplinary issues.  Now, I'm no snitch, I try to avoid stitches when possible.  But I <em>do</em> like making processes more efficient.   </p>

<p>      The HR person who brought the idea up stated that a previous job had a word document that acted as the form.  Let's not get it twisted, we <em>could</em> do that... But that would mean diving into visual basic programming.</p>

<p>     From MY previous last job, I made an excel macro that would send out emails reminding people to update their documents.  It was fun enough, I suppose, but learned quickly that VB and I don't get along.</p>

<p>Instead, I decided to leverage my web developments skills and make a standalone web form. </p>

<p>Let's look at the user story:<br>     Ability to enter the info info of the manager, employee, incident, what actions were taken.<br>     Display the actual wording from the company manual.<br>     Have the form remind everyone what the next course of action would be depending on the actions / issue on the form.<br>     Be able to email / print form as a PDF.</p>

<p> This is the final product:</p>

<p class="has-text-align-center"><a href="https://codepen.io/melvinhicklin/pen/ExaJzMV">CodePen.io</a></p>

<p>Basic looking? Yes.  But we don't need <em>fancy</em>, we just need <em>functional</em>, Fancy can always come later.  </p>

<p class="has-text-align-center">Of course, feel free to use this form and change it around to fit your purpose.  <br>You can put lipstick on this pig and sent it to the rodeo in your version.  </p>

<p>     Overall, It's a simple form but there are a few things I want to want to point out.  Our current environment uses Chrome as an alternative browser, So a chrome shortcut that would pull up the page directly from a place on our network:<br>"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" file:///&lt;File location&gt;<br>    This gives me the added benefits of native PDF printing along with being able update in the background and users not noticing.<br>Starting at the top we have:</p>

<ul><li>Date and time stamp<ul><li>Simple JavaScript, but I discuss it below.</li></ul></li><li>Drop down menus for the department affected</li><li>Text fields for Associate and Manager names</li><li>Drop down menus for prior and current warnings<ul><li>Selecting Prior auto-fills the current warnings.  Discussed below.</li></ul></li><li>Drop down menu for policy the was violated<ul><li>Fills in an area to show policy  </li></ul></li><li>Button to reset policies<ul><li>I'll discuss that in a bit</li></ul></li><li>Text field to describe how the policy was broken</li><li>Area for the policy selected before is displayed</li><li>Drop down menu for next course of action</li><li>Signature area</li><li>Check and Print button<ul><li>Discussed below </li></ul></li></ul>

<p>The form is simple but I wanted to draw back the curtain and show some of the mechanics behind it:</p>

<p><strong>Date and Time Stamp</strong><br>A DIV element, ID of 'dateF' short for 'date field', will hold the date:<em><strong>  var d = new Date();</strong></em><br>We take that variable and replace the inner HTML of the DIV element to the string "Date and Time" and concatenate the 'd' variable, here translated into a string with the .toLocaleString method, to the end.<br><strong><em>document.getElementById("dateS").innerHTML = "Date and Time: "+d.toLocaleString();</em></strong></p>

<p><strong>Autofill Prior and current warnings</strong><br>Streamlining the process is a major priority when I make a project.  For me that means automating the redundant, the boring and the annoying little stuff.  Nothing sucks more then having someone introduce a new thing to do resulting in more paper work to do and more boxes to check.  To that end, Making the form as easy as possible means the end users will be willing to accept into their work flow.<br><br><em><strong>f</strong></em><strong><em>unction autoFillCurrentWarning(priorWarning) {<br>     var warningToInterger = parseInt(priorWarning, 10);</em></strong><br>//<strong><em><br>     var nextStep = warningToInterger + 1;</em></strong><br>//This is where the 'magic' starts.  The var priorWarning represents what is selected in the Prior Warning field.  Because it comes into autoFillCurrentWarning as a string, we have to use parseInt (Syntax: parseInt(Varible Name, Radix) Radix is the numerical system to use 2 = binary, 10 = demical) turning the string into an integer where we can increament it by 1.  <br>Note: 'i++' could have been used, but I didn't feel like it. <strong><em><br></em></strong><br><strong><em>     var curWarning = document.getElementById("currentWarnSelection");<br>          curWarning.value = nextStep.toString();</em></strong><br>//This part takes the integer, places it inside a variable and turns it back into a string.  Once there, it completes the autofill function.  However, inside the form I have a couple of date fields that are suppose to show up if certain warning types come up.  To make sure those fire off, I added an IF statement:<strong><em><br>                if (nextStep &gt;= 3) {<br>                    suspend(nextStep);<br>                }</em></strong><br>//This calls the 'suspend' function and ensures the date fields display.<strong><em><br>}</em></strong></p>

<p><strong>Drop down menu for policy the was violated</strong><br>The request to have the company policy appear when it's selected from the drop down menu could be better much more efficiently but for this form I ended up using a quick method.  The DIVs holding the policies are hidden with CSS: display:none;<br>When a policy is selected from the dropdown, the onChange passes what was selected:<br><strong><em>select id="polVioC" class="drop" onchange="polVioSelect(this.value)"</em></strong></p>

<p>The JS function polVioSelect adjusts the CSS based on the DIVs id:<br><strong><em>function polVioSelect(polVioChoice) {<br>     var pick = polVioChoice.toString();<br>          if (pick == "safe" || "unac" || "time1" ||"time2" || "unsat" || "other" || "hara" || "sex") </em></strong><br>//I know there is a better way to set this up, but this was the best solution <em>I</em> could come up with.  If I find a better way to refactor, I would like to revisit it.<br><strong><em>{<br>               document.getElementById(polVioChoice).style.display = "block";<br>          }<br>}</em></strong></p>

<p><strong>Button to reset policies</strong><br>So, due to a lack of knowing everything, I ended up making a button to clear out the policy area.  The button adjusts the CSS back to display:none for all the DIVs that have display:block.  It can act a little weird every once in a while but it gets the job done. </p>

<p><strong>Notes about @media</strong><br>The buttons are part of a CSS group that turns them to display none while printing:<br><strong><em>@media print{<br>     print{<br>          display:none;<br>     }<br>     reset{<br>          display:none;<br>     }<br>}</em></strong><br>@media allows you to make special CSS groups for different screen types.  You may want your page to display different on a tablet verses a cellphone verses a desktop.  Here we are saying 'When we print this page, the buttons will not be displayed'.</p>

<p><strong>Submit button</strong><br>Normally the submit button is attached to a PHP action and will run validation checks before giving it to the server.  For this, I added a 'Check and Print' button and made a simple Javascript function for the button to call.  If everything is filled in, the print window pops up.  If something is missing, a pop up notifies the user that a field needs attention.  First we add a .onsubmit event listener to call our Javascript function (checkAndSubmit):<strong><em><br>document.getElementById("discipline").onsubmit = function() { checkAndSubmit(); };<br></em></strong><br>Then our actual function goes off:<br><strong><em>function checkAndSubmit() {<br>event.preventDefault();<br></em></strong>//This prevents the default function of 'submitting and resetting' the form.<br><strong><em>window.print();<br></em></strong>//This is the actual print function called.<br><strong><em>return false</em></strong>;<br>//No info is being returned, so we set this to false.<br><strong><em>}</em></strong></p>

<p><strong>What did we learn / TL;DR</strong><br>Made a HTML 5 Discipline form.  Names have been changed to protect the innocent.  Learned a couple neat tricks: <br>Auto-filling drop down menus.<br>Having HTML form checking with JavaScript.<br>Making Buttons disappear when printing.</p>

