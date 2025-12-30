---
layout: post
title: Math Game - Minimum Variable Product
date: 2020-01-01 18:30
author: k3ntuckyblog
comments: true
categories: [Game Design, Math, Math Quest, MVP, Programming]
---

<p class="has-text-align-center">-Or-<br>Designing a game without knowing Game Design.</p>

<p>When I first started this blog, I had every intention of documenting a game I was making.  It's not a huge game, more accurately what I have now is more a piece of a game.  I made the game up to a point and life did it's usual thing and the project kind of got put on the back burner.  </p>

<p>Recently a friend of mine expressed interest in designing a game so I figured I would return to my old first game.  This is a slight repost, but it's new if you missed it the first time.</p>

<p>So... Where to begin?  The title would a good start, I plan to call this game:</p>

<p><strong>MATH QUEST</strong></p>

<p>Wait, Don't go! Hear me out...</p>

<p>I've always liked the Nintendo DS game "Brain Age", particularly the mini-game where you see how many simple math questions you can get correct within the time limit. I find it very satisfying just to see how far I can go. Confession: I can't play this game just <em>once</em>. I usually end up taking a warmup turn, a loosen up turn, elevenies, and an extra round to make sure the last one wasn't a fluke, then (if needed) a final round as a tie-breaker.  </p>

<p>If you were to break down the game play loop of this mini game it would look something like this:<br>Start<br>Get problem<br>Solve<br>reset until either hero or enemy hp is 0.</p>

<p>Starting with that as the foundation, I wanted to see if I could expound upon the idea.  Hopefully create something to make math more accessible by gamifying it.</p>

<p>But where should we start?  I'm not a game designer (note the title of this post), I would say I have a good foundation in the basics of programming, mainly with JavaScript.  So using the tools at my disposal, we will make a simple JavaScript game.</p>

<p>The usual starting points (Online courses, books, boot camps) like to get you into the "Coding" of a specific type of game more than the actual “Design” of a game.  This is a fine starting point for people with no programming experience who can learn the basic by doing rather then reading.  For a while I felt like I understood the concept but not how to apply them, but I didn't know what to do with them.</p>

<p>Pretty soon the idea burn out cycle starts,  Early ideas start to get too big to do anything but fail. The basic idea grows and killer features get added and soon the idea is too big to prototype or maybe it gets too technical for our current skill set.  Then the burn out sets in before we've had a chance to work on it.  Next thing we know, we're walking away defeated and our confidence is shaken.  But this time, before we think about the finished product, we will keep the idea small and manageable. To do that, we will make an Minimum Variable Product (MVP).</p>

<p>Once I learned about MVPs, not only did I start making progress in my game, I started learning beyond the basics of programming by leaps and bounds. An MVP is the most basic explanation of your product. Much like the game play loop for the math minigame above, an MVP would be the bare minimum for playing 1 round of your game.</p>

<p>Take a game like Street Fighter:<br>2 characters, moving left and right, hit each other. When one player connects enough hits, they are the winner.</p>

<p><em>But K3ntucky, there's also jumping, blocking, high / med / low kicks and punches, the super moves, all the different characters?  Why didn't these get mentioned?</em>  <em>These are basic parts of a fighting game as well, aren't they?</em></p>

<p>Of course there's more, but Street Fighter explained as an MVP is just 2 characters hitting each other until a winner is declared.  An MVP will leave out many details and mechanics for the sake of making the explanation as simple as possible.  Once you have the MVP working you can to flesh out / expand the overall idea adding all the wild ideas to make your game unique.  <strong>No one is born running, we all crawl before we walk.</strong></p>

<p>To get a better idea of what an MVP entails, check out this video from a channel called Extra Credits.  They cover a variety of topics, mainly video games and world history.  This video explains the concept very well and is, so far, the best starting point I've seen when it comes to game design for the absolute beginner:</p>
<!-- wp:embed {"url":"https://www.youtube.com/watch?v=z06QR-tz1_o","type":"video","providerNameSlug":"youtube","responsive":true,"className":"wp-embed-aspect-16-9 wp-has-aspect-ratio"} -->
<figure class="wp-block-embed is-type-video is-provider-youtube wp-block-embed-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio"><div class="wp-block-embed__wrapper">
https://www.youtube.com/watch?v=z06QR-tz1_o
</div></figure>
<!-- /wp:embed -->
<p>So the big question…  In the barest-bone explanation, what's the MVP of my game?</p>

<p>The MVP of my game, much like the brain age mini game from earlier, would be answer math problems.  Very basic but it gives us a foundation to create then expound upon.  Of course to make the MVP a reality, we'll need a few components. <br>Play area<br> -Randomly generated problem<br> -Randomly generated possible answers<br><br>Game Logic<br> -Calculate answer to problem<br> -Compare calculated answer against user selected answering<br> -Calculate correct answers (ca) and wrong answers (wa) / store amount of ca and wa<br> -When ca or wa reach a number, declare winner.</p>

<p>With this MVP plan in place, I can make simple milestones to work toward and allows me a better idea of the progress I'm making.  </p>

<p>With your MVP in place, you make every milestone a little victory that keep you progressing to bigger things and I that is something I hope readers take away from these posts.</p>

<h2 id="tl-dr">TL;DR</h2>

<p>-One part of this blog is about documenting my thoughts while I work on a game called Math Quest.<br> -This video from <a href="https://www.youtube.com/watch?v=z06QR-tz1_o">Extra Credits</a> is a great starting point to people who are literally new to game design.<br> -The Minimum Viable Product is an important concept to consider in design to keep focus and prevent burnout.<br> - Small victories keep us wanting to learn more and small steps over time equal great distances.</p>

