---
layout: post
title: HTML - Making a grid
date: 2019-03-03 13:05
author: k3ntuckyblog
comments: true
categories: [CSS, Game Design, HTML Design, Javascript, Math Quest, Projects]
---
<p>For my game, MATH QUEST, I need to design how a round of the game will play.  It doesn't have to be pretty at this point, just functional.</p>
<p>Basically I'll need a way to make a </p>

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center"><a href="https://codepen.io/melvinhicklin/details/a4356e7eb117fce95bb721bdee6db9f0">Check out my CodePen for making grids.</a><br>These examples make a 3x3 grid, but they can be edited to other grid sizes. Just edit the lvl.l0 object at the top of the JavaScript page.<br><a rel="noopener noreferrer" target="_blank" href="https://code.sololearn.com/WqGfEhUZfHct/#html">Try it over here on SoloLearn.</a><br><br>Note the differences between running code in Codepen vs Sololearn. <br>In future development we will need to take the environment your code runs into account to make sure it executes consistently.</p>
<!-- wp:heading {"level":3} -->
<h3>General Design Overview</h3>
<!-- /wp:heading -->
<p>The elements generated for the grid will have different IDs but all in the same class.&nbsp; The class handles the look and the IDs allow the JavaScript to interact with the individual elements.</p>
<!-- wp:heading {"level":3} -->
<h3> Nested Loop </h3>
<!-- /wp:heading -->
<p>For those not in the know, a nested loop is a loop within a loop.  Our first loop (Outside loop) will execute once, then our second loop (Inside loop) will execute it's set number of times before going to the first loop again for it's number of times to execute.<br><br>Our nested loop starts by making a table row &lt;tr&gt; element, we attach an id to it (Quick Note: The ids for both the Table Row &lt;tr&gt; and Table Data &lt;td&gt; elements are "row" concatenated with the outer loop iteration or "box" concatenated with the box count, respectively.), then we make it a member of the "row" class.  </p>

<p>Finally we append it to the JavaScriptLoopArea &lt;table&gt; element. At this point, the second loop will make x boxes, give them an id, attach the "box" class and append those elements to the &lt;tr&gt; element with an id equal to the row.id variable inside the table element.  To control the number of rows and boxes, We have 2 variables setup inside a JavaScript object, x and y.&nbsp; x will be how many rows we have while y will be how many boxes will be made.<br><br>At this point, if you're looking at the one of the examples, you can open your web developer tools (F12 is pretty much the go to key these days for web development tools now a days) and see that we have 3 &lt;tr&gt; elements labeled 1, 2, 3.&nbsp; Expand those rows and we'll see 3 elements labeled 1,2,3 inside each row.<br></p>
<!-- wp:heading {"level":3} -->
<h3>CSS Grid</h3>
<!-- /wp:heading -->
<p>CSS Grid is definitely something you want to start learning; if you haven't already.  It's easy to use and can make complex fluid layouts quickly.  With positioning and sizing handled by CSS grid, our javascript just needs to make the elements.  We will need to know what grid sizes we offer to the player, Each grid size will need a corresponding CSS entry.<br><br>Inside the Example(s), I commented some fake CSS entries, .CssExample1, .CssExample2, .CssExample3.  These entries are just some additional examples I wanted to since this example uses CSS grid as an id.  <br><br>Since all we need is a set number of blocks, I changed our JavaScript to a simple loop that just makes elements and assigns them IDs and Classes.  The elements will have the same classes as before ("Rows" and Boxes").<br><br>We have a variable called steps in our JavaScript object to dictate the amount of elements created.  The boxes get an id and class like before, and CSS grid handles positioning and everything gets appended to the CssJavaScriptArea element.<br><br>Check out the development tools for this grid as well.  Nothing special to note in the code itself but seeing the structure how the structure are made may help solidify how the JavaScript is written vs what JavaScript creates.</p>
<!-- wp:heading {"level":4} -->
<h4>Mistakes were made</h4>
<!-- /wp:heading -->
<p>For some extra credit, figure out what is happening in our third example.&nbsp; This is a mistake that I came across when making the examples.&nbsp; Instead of concatenating the words "row" or "box", I had the ids of all the rows and boxes as numbers (row.id=1 box.id=1, row.id=2, box.id=2 so on..).&nbsp; So while the loops occur, JavaScript kept appending the elements to the wrong rows and data.  It ended up being an interesting logic error (logic error meaning the code still functions, just not in the way it was intended), If the CSS JavaScript grid is created, the mistake grid will show up within the CSS grid. If the CSS grid isn't created then it will show up in it's own area.</p>
<!-- wp:heading {"level":3} -->
<h3>Final Verdict:</h3>
<!-- /wp:heading -->
<p>Overall, both methods are perfectly fine and serve their purposes.  So how do we choose?  That really depends more of what you are looking for.  I ended up using the Nested Loop because of the flexibility. Being able to control both the rows and boxes can  allow for some interesting developments down the road. <br></p>

<p><strong>Nested Loop:</strong><br>The nested loop allows us to adjust the size to what we want, Even 4x2 or 3x9 grids can be easily setup by just adding or editing the object numbers.</p>

<p><strong>CSS Grid:</strong><br> CSS Grid makes positioning elements easy and can give us some options to play around with the positioning and sizes different parts of the grid, if our game called for it;  Positioning and sizing, at least for this game, isn't a priority. Combined with the need to make CSS entries depending on how many sizes of grid you want / expect to have, leads me to feel this method is more suited to a game with a static number of elements.</p>
<!-- wp:heading {"level":3} -->
<h3>TL:DR;</h3>
<!-- /wp:heading -->
<p>We have 2 ways to make a grid:<br>&nbsp; &nbsp; &nbsp;-Using CSS Grid and JavaScript<br>&nbsp; &nbsp; &nbsp;-Nested Loop<br><br>Links to examples:<br><a rel="noopener noreferrer" href="https://codepen.io/melvinhicklin/details/a4356e7eb117fce95bb721bdee6db9f0" target="_blank">CodePen.io</a> / <a rel="noopener noreferrer" target="_blank" href="https://code.sololearn.com/WqGfEhUZfHct/#html">SoloLearn</a><br></p>

