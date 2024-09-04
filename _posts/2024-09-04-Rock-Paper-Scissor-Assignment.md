---
title: Rock Paper Scissors Lizard Spock - A Developer's Challenge
description: Job's position assignment.
author: 999999	
date: 2024-08-08 12:12:00 +0800
categories: [Blogging, Interview]
tags: [interview, typescript]
pin: true
math: true
mermaid: true
image:
  path: /assets/posts/2024/POST-ID-1/mobile-rules-modal-bonus.jpg
  alt: The Rules of Rock Paper Scissors Lizard Spock.
---
<!-- POST-ID-1 -->
# A Developer's Challenge[^footnote]
{: .mt-4 .mb-0 }

The classic game of Rock Paper Scissors has been a staple of playgrounds and social gatherings for generations. However, in 2005, The Big Bang Theory's Raj Koothrappali and Sheldon Cooper introduced a new twist to the game: Rock Paper Scissors Lizard Spock. This expanded version of the game adds two new hand signals, "Lizard" and "Spock," and a new set of rules to govern their interactions.

As a developer, you may be wondering how to tackle this problem and create a program that can play Rock Paper Scissors Lizard Spock. In this article, we'll explore the rules of the game, discuss possible approaches to solving the problem, and provide a sample implementation in Typescript.

The interview assignment focuses on resolving the problem of determining the winner using various methods, and delves deep into: coding skills, code patterns, live coding, and problem-solving approaches 

- Front-End Framework using ReactJS
- Back-End NodeJS and dependencies

## Capture of given assets

Of couse every assignment would not be in happy path :cry:
![Desktop View](assets/posts/2024/POST-ID-1/ScreenShot-1.jpg){: width="972" height="589" }
_Built and run_


![Desktop View](assets/posts/2024/POST-ID-1/ScreenShot-2.jpg){: width="972" height="589" }
_After hours of reading and fixed everything now in place_


### Approaches to Solving the Problem

1. If-Else Force 
```Typescript
export const winner = (player1: string, player2: string): string | undefined => {
	let winner: string = '';

	if (player1 === 'scissors') {
		if (player2 === 'scissors') winner = 'draw';
		else if (player2 === 'paper' || player2 === 'lizard') winner = player1;
		else winner = player2;
	} else if (player1 === 'paper') {
		if (player2 === 'paper') winner = 'draw';
		else if (player2 === 'rock' || player2 === 'spock') winner = player1;
		else winner = player2;
	} else if (player1 === 'rock') {
		if (player2 === 'rock') winner = 'draw';
		else if (player2 === 'lizard' || player2 === 'scissors') winner = player1;
		else winner = player2;
	} else if (player1 === 'lizard') {
		if (player2 === 'lizard') winner = 'draw';
		else if (player2 === 'spock' || player2 === 'paper') winner = player1;
		else winner = player2;
	} else if (player1 === 'spock') {
		if (player2 === 'spock') winner = 'draw';
		else if (player2 === 'scissors' || player2 === 'rock') winner = player1;
		else winner = player2;
	} else winner = 'draw';

	return winner;
};
```
2. Modular Arithmetic Approach

```Typescript
import { SIGN } from 'types'

export const rules = {
	[SIGN.PAPER]: new Set([SIGN.ROCK, SIGN.SPOCK]),
	[SIGN.ROCK]: new Set([SIGN.SCISSORS, SIGN.LIZARD]),
	[SIGN.SCISSORS]: new Set([SIGN.PAPER, SIGN.LIZARD]),
	[SIGN.LIZARD]: new Set([SIGN.SPOCK, SIGN.PAPER]),
	[SIGN.SPOCK]: new Set([SIGN.ROCK, SIGN.SCISSORS]),
}
```

```Typescript
import { SIGN } from 'types'

export const rules = {
	[SIGN.PAPER]: new Set([SIGN.ROCK, SIGN.SPOCK]),
	[SIGN.ROCK]: new Set([SIGN.SCISSORS, SIGN.LIZARD]),
	[SIGN.SCISSORS]: new Set([SIGN.PAPER, SIGN.LIZARD]),
	[SIGN.LIZARD]: new Set([SIGN.SPOCK, SIGN.PAPER]),
	[SIGN.SPOCK]: new Set([SIGN.ROCK, SIGN.SCISSORS]),
}
```

3. Polar Coordinate System  - My approaching for more than 5 choices


```text
Number of possible cases, we can multiply the number of choices for each player
- 5 choices = 5*5 = 25 total cases

	2-D Array from 360/5 = 72 degree for each choice
	
	1 Radian = 180/π  = 57.296 Deg
	2π 	* rad   			= 360
	2π/3 * rad 				= 120 deg
	π/3 	* rad  			= 60  deg
	
	1 Degree = degree * π/180 = 0.0174 Radial

- List of choices would be [2π/5, 4π/5, 6π/5, 8π/5, 2π]

- Following game's rules checking the angle of 2 choices

	If Choice-1 === choice-2 => Draw
	(If both choices from same position)
	
	--- Circular rule ---
	If |choice-1 - choice-2|   == 2π/5 => choice-1 win 
	(check user's choice at X-position - 72 degree => Y-position of computer's choice => that's mean user's winning)

	If |choice-2 - choice-1|   == 2π/5 => choice-2 win
	(check computer's choice at X-position - 72 degree => Y-position of computer's choice => that's mean computer's winning)

	--- Hexagon rule ---
	If choice-1 - 2π/3*rad = choice-2 => chocie-1 win
	(Check angles of both choices in between 144 Degree)
```

```css

/* Angles - The use of some css preprocessor would be nice for iteration*/
.deg72 {
	position: absolute;
	transform: rotate(72deg) translate(145px) rotate(-95deg);
}
.deg144 {
	position: absolute;
	transform: rotate(144deg) translate(145px) rotate(-144deg);

}
.deg216 {
	position: absolute;
	transform: rotate(216deg) translate(145px) rotate(-216deg);

}
.deg288 {
	position: absolute;
	transform: rotate(288deg) translate(145px) rotate(-288deg);

}
.deg360 {
	position: absolute;
	transform: rotate(360deg) translate(145px) rotate(-360deg);

}

```


#### Finalize

So, the easiest way to implement the function to detect a winner would be the 1st and 2nd options.

The advantage of the 3rd solution is that it allows to extend to many many choices and for a more consistent implementation of the UI and solution, but this would be more suitable for requirements that can be handled on the client's side. Some calculations would need to be placed on the server's side.

To keep things simple and easy, as the assignment requires, we should choose the 1st and 2nd options to make the code more consistent, rather than opting for the complexity of the 3rd way


[^footnote]: Back to top
