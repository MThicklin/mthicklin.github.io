---
layout: post
title: Business Card Generator
date: 2019-07-04 13:27
author: k3ntuckyblog
comments: true
categories: [CSS, Fun Web Projects, HTML, HTML Design, Javascript]
---

<p>In the British TV series Doctor Who, The Doctor has a couple of toys at his disposal to save the day.  People familiar with the series know of the sonic screw driver, but not everyone remembers / knows about the Psychic Paper, which I feel is under appreciated.</p>

<p>Psychic Paper can psychically display important looking papers to whoever looks at.  Something about having the ability to gain instant legitimacy intrigues me.  </p>

<p>With this in mind, I got the idea for a project: The Business Card Generator (BCG).  It's purpose is to create instant business cards.  Excellent for forging new identities or adding instant legitimacy without all that experience mess getting in the way.  A business card may not seem like an important item, but I think in the right hands, they could be indispensable.</p>

<p class="has-text-align-center">Click here for the <a href="https://codepen.io/melvinhicklin/full/YOpaXp">codepen.io</a> project.</p>

<h2>HTML:</h2>

<p>The BCG interface is meant to look like a pile of cards.  The 'focus' div contains 2 divs ('main' and 'sub').  These will display a name (main) and job title (sub).  2 additional divs ('name' and 'job') in the back will act as event handlers to generate a new name or job.</p>

<p>Div setup:<br>Focus<br>|<br>Main - sub<br>Name  - Job</p>

<h2>CSS:</h2>

<p>Nothing really fancy with the CSS for this project.  But I want to mention the use of z-index, which indicates where a div is in a stack.  The higher the number,  the higher on the stack your element will be.  Negative numbers work here, so our top div "Focus" with a z-index of 0 and the divs "name" and "job" have z-indexs -1 and -2, respectively.  Divs "name" and  "job" then get rotated ('transform: rotate(10deg)' &amp; 'transform:  rotate(-10deg)') to give the impression, I hope, of cards poking out out  of the stack.  I think it worked out pretty well.</p>

<p>focus {<br>   border: 5px solid black;<br>   z-index: 0; <br><em>//z-index stacks the divs on top of each other. The higher the number, the higher on the stack you go."Focus" has a z-index of 0 is it will be on top.</em><br>}<br>name {<br>transform: rotate(10deg);<br>   text-align: left;<br>   z-index: -1; <br>/<em>/This div is below "Focus" and above "job"</em><br> }<br>job {<br>transform: rotate(-10deg);<br>   text-align: right;<br>   z-index: -2;<br><em>/*This div is below 'name'.*/</em><br>}</p>

<h2>JavaScript:</h2>

<p>JavaScript handles the random names / jobs and their placement in the appropriate divs when the user clicks on either 'new name' or 'new job'.</p>

<p>The "name" &amp; "job" divs have event listeners to the appropriate functions:<br>document.getElementById("name").addEventListener("click", ranName); document.getElementById("job").addEventListener("click", ranJob);</p>

<p>When the functions start, they create variables. Depending on the function selected, All but one of them will be initialized as a random index on their array.  </p>

<p>To access an index of an array like this:<br>var j = job[0]; //Arrays are zero-based with 0 is first, 1 is second, 2 is third, etc...</p>

<p>To access a random index of our arrays, we will use this:<br>var job = job[Math.floor(Math.random()*job.length)];<br>Math.random()*job.length generates a number based on how many items are inside array.  Then Math.floor() will round the number down (For those wondering, Math.ceiling is used to round the number up). </p>

<p>The ranJob function initializes 'j' as a random index of the job array.  .innerHTML then clears out the 'sub' div and replaces it with the contents of j.</p>

<p>The ranName function starts by creating fName and lName as random indexes of the 'fi' and 'la' arrays. (First Name &amp; Last Name, respectively).  The variable fullName concatenates fName, a space and lName.  With .innerHTML clearing out the 'main' div and placing the contents of fullname in it.</p>

<p>All together we have:<br>document.getElementById("name").addEventListener("click", ranName);<br>document.getElementById("job").addEventListener("click", ranJob);<br><br>var fi = ["John", "Sam", "Donny", "Greg", "Derrick", "Chris", "Todd", "Frank", "Boxy"];<br>var la = ["Smith", "Tibbs", "Nackle", "Odom", "Seitz", "Goldman", "Doodle", "Brown"];<br><br>var job = [<br>"Plumber",<br>"Whale Scrubber",<br>"Pianist",<br>"Generally Good Person",<br>"Has more money in his pocket then you",<br>"Duke of New York"<br>];<br><br>function ranName() {<br>"use strict";<br><em>//First and last names are generated here…</em><br>var fName = fi[Math.floor(Math.random() * fi.length)];<br>var lName = la[Math.floor(Math.random() * la.length)];<br><em>//and concatinated here.</em><br>let fullName = fName + " " + lName;<br><em>//and inserted into the HTML here.</em><br>document.getElementById("main").innerHTML = fullName;<br>}<br><br>function ranJob() {<br>"use strict";<br><em>//The jobs are generated here.</em><br>var j = job[Math.floor(Math.random() * job.length)];<br><em>//and inserted into the HTML here.</em><br>document.getElementById("sub").innerHTML = j;<br>}</p>

<h2>What did we learn / TL;DR:</h2>

<p>Fun stuff, right?  Learning how to apply JavaScript arrays and random numbers.  Good times.  </p>

<ul><li><a href="https://codepen.io/melvinhicklin/full/YOpaXp">Codepen.io Example</a></li><li>JS variables can be initialized as an index in an array:<br>     var j = &lt;name of array&gt;[0].</li><li>JS variables can be initialized as a random part of an array:<br>     var job = &lt;name of array&gt;[Math.floor(Math.random()*job.length)]; </li><li>Math.floor() rounds down, Math.ceiling() rounds up.</li><li>Math.random()*&lt;name of array&gt;.length will generate a number between 0 and the size of your array.</li></ul>

