---
layout: post
title: Business Card Generator
date: 2026-01-02 21:27
author: k3ntuckyblog
comments: true
categories: [CSS, Fun Web Projects, HTML, HTML Design, Javascript]
---

In the British TV series Doctor Who, the titular character, The Doctor, has a couple of toys at his disposal to save the day.  People familiar with the series know of the sonic screw driver, but not everyone remembers / knows about the Psychic Paper, which I feel is under appreciated.

Psychic Paper can psychically display important looking papers to whoever looks at.  Something about having the ability to gain instant legitimacy intrigues me.  

With this in mind, I got the idea for a project: The Business Card Generator (BCG).  Excellent for forging new identities or adding that touch of instant legitimacy without all that experience mess getting in the way.  Business cards may not seem like an important item, but I think in the right hands, they could be indispensable.

[Click here for a replit of the finished project.](https://replit.com/@K3ntucky/Business-Card-Generator)

## The HTML

The BCG interface is meant to look like a pile of cards.  The 'focus' div contains 2 divs: 'main' to display the name and 'sub' to display the job. 2 additional divs ('name' and 'job') in the back will act as event handlers to generate a new name or job.

Div setup:Focus|Main - subName  - Job

## The CSS

Nothing really fancy with the CSS for this project.  But I want to mention the use of z-index, which indicates where a div is in a stack of divs.  The higher the number, the higher on the stack your element will be. The top div "Focus" with a z-index of 3 and the divs "name" and "job" have z-indexs 1 and 2, respectively.  (Originally I had the Focus element as 0, with Name and Job as -1 and -2, but this ended up causing issues as the name and job elements were under the focus element but on some browsers they were considered covered.)  Divs "name" and  "job" then get rotated ('transform: rotate(10deg)' & 'transform:  rotate(-10deg)') to give the impression, I hope, of cards poking out out  of the stack.  I think it worked out pretty well.

>focus {border: 5px solid black;   z-index: 3;}
>name {transform: rotate(10deg);   text-align: left;   z-index: 1;}
>job {transform: rotate(-10deg);   text-align: right;   z-index: 2;}

## The JavaScript

JavaScript handles the random names / jobs and their placement in the appropriate divs when the user clicks on either 'new name' or 'new job'.

The "name" & "job" divs have event listeners to the appropriate functions:document.getElementById("name").addEventListener("click", ranName); document.getElementById("job").addEventListener("click", ranJob);

When the functions start, they create variables. Depending on the function selected, All but one of them will be initialized as a random index on their arrays.  

To access an index of an array like this:var j = job[0]; //Arrays are zero-based with 0 is first, 1 is second, 2 is third, etc...

To access a random index of our arrays, we will use this:var job = job[Math.floor(Math.random()*job.length)];Math.random()*job.length generates a number based on how many items are inside array.  Then Math.floor() will round the number down (For those wondering, Math.ceiling is used to round the number up).

The ranJob function initializes 'j' as a random index of the job array.  .innerHTML then clears out the 'sub' div and replaces it with the contents of j.

The ranName function starts by creating fName and lName as random indexes of the 'fi' and 'la' arrays. (First Name & Last Name, respectively).  The variable fullName concatenates fName, a space and lName.  With .innerHTML clearing out the 'main' div and placing the contents of fullname in it.

All together we have:
>document.getElementById("name").addEventListener("click", ranName);
>document.getElementById("job").addEventListener("click", ranJob);
>var fi = ["John", "Sam", "Donny", "Greg", "Derrick", "Chris", "Todd", "Frank", "Boxy"];
>var la = ["Smith", "Tibbs", "Nackle", "Odom", "Seitz", "Goldman", "Doodle", "Brown"];
>var job = ["Plumber","Whale Scrubber","Pianist","Generally Good Person","Has more money in his pocket then you","Duke of New York"];
>function ranName() {"use strict";//First and last names are generated here…
>var fName = fi[Math.floor(Math.random() *fi.length)];
>var lName = la[Math.floor(Math.random()* la.length)];//and concatinated here.
>let fullName = fName + " " + lName;//and inserted into the HTML here.
>document.getElementById("main").innerHTML = fullName;}function ranJob() {"use strict";//The jobs are generated here.
>var j = job[Math.floor(Math.random() * job.length)];//and inserted into the HTML here.
>document.getElementById("sub").innerHTML = j;}

## What did we learn / TL;DR

Fun stuff, right?  Learning how to apply JavaScript arrays and random numbers.  Good times.  

- [Replit Example](https://replit.com/@K3ntucky/Business-Card-Generator)
- JS variables can be initialized as an index in an array: `var j = <name of array>[0]`
- JS variables can be initialized as a random part of an array: `var job = <name of array>[Math.floor(Math.random()*job.length)]`
- `Math.floor()` rounds down, `Math.ceiling()` rounds up.
- `Math.random()*<name of array>.length` will generate a number between 0 and the size of your array.
