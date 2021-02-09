---
layout: default
title: Testing
parent: Documentation
---
# Testing

[Deliverable (.pdf)](../../assets/deliverables/current/Test2.pdf){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

## Summary of testing methods and approach
In continuing the code base started by team 10, the Brownfield project presented many problems associated with testing. The main problem with the code is that a lot of the logic for the game is decided within the function “Game.render()” without good use of OOP. Some logic that should be decided within individual classes (such as what happens after boats collide with objects) are explicitly stated within Game.render rather than in the respective classes in their own functions. 

Given more time we would rather change the base code to apply better programming standards but given the short time constraints we decided to try and work around it instead and leave it as legacy code. This, however, makes testing the logic for the game functional and stable difficult as many of the key functions of the program are in one large method that depends on many variables and classes that are not explicitly stated as parameters.

Furthermore, the project we picked up was using “libgdx” to handle the graphical interface and drawing to the screen. This seemed like an easy library to work with at the start however resulted in conflicts with testing as “org.JUnit...” cannot be imported into a file that also imports “com.badlogic.gdx...” as they both require initialisation that must be completed before the other is done. There are definitely work arounds for this, but the most simple solution that we chose was to do as much automatic testing with JUnit as possible but to perform our own tests for any files, classes and functions that reference any classes related to “libgdx”. In essence our aim was to recreate the functionality of automatic testing that comes from JUnit but using print lines to the terminal that showed the result of the tests.

## Unit Testing

|Test ID|Test Name|Function / Class Being Tested|Purpose of Test|Result of test
|1|BoatFinished|Boat.hasFinished|To test whether the game registers that a boat correctly finishes the race.|Pass
|2|ObstacleInRange|AI.obstacleInRange|Test whether an obstacle is close enough in range to dodge by saying the obstacle is close in front of the AI boat|Pass
|3|Leg Increase Difficulty |GameData.level|To see whether the game gets more difficult after each leg|Pass
|4|Unique Boats|Boats|To check whether each boat has unique stats|Pass

## Manual Testing

Evidence for these tests were recorded as videos. In the evidence columns are links to the videos. 
Master playlist:https://youtube.com/playlist?list=PLeiypr_FdgV4qvlrpTOew1ohpvV5T2nP3 


|Test ID|Test Name|Function / Class Being Tested |Purpose of Test|How the test was performed|Inputs|Expected Outputs|Actual Outputs|Pass/Fail|Evidence|Author
|5|InputTest|Game.keyup/keydown|To test whether the game registers key presses correctly.|Run the game and press the keys A, D and ESC to test they work|A, D and ESC key|A key turns the boat left, D key turns the boat right and ESC brings up the pause menu|A key turned the boat left, D key turned the boat right and ESC brought up the pause menu|Pass|https://youtu.be/yf-7r1VLPQg |Ayyesha
|6|ObstaclesSpawn|Lane.spawnObstacles|Test to see that obstacles spawn and have a collision body|Start the game at any difficulty and check if obstacles spawn, and they have a collision body|n/a|Obstacles will spawn and have a collision body|Obstacles spawned and had a collision body|Pass|https://youtu.be/Y0bF0Nbwbws |Ayyesha
|7|Difficulty|MenuUI|Test that the game on medium is harder than the game on easy, and the game on hard is harder than the game on medium.|Load the game on easy, medium and hard difficulties to check the difference in difficulties|n/a|The difficulty increases as it’s supposed to|The difficulty increased|Pass|https://youtu.be/XP8ER6QmVYA |Ayyesha
|8|SaveGame|SaveGame|To test whether the save game functionality works|Start a game on any difficulty. Pause the game before the race is over and exit to the menu, then exit the game. Then reopen the game and load the last saved game|n/a|After loading the last saved game, the correct game is loaded and resumed from where the player left off|The right game was loaded and resumed at the correct point|Pass|https://youtu.be/9owEq5hzSbg |Ayyesha
|9|BoatMoved|Boat.moveBoat|To check that the boat moves when the speed > 0.|Run the game on any difficulty and see if the boat moves|n/a|Boat moves forward|Boat moved forward|Pass|https://youtu.be/szhmpVJja9w |Ayyesha
|10|TimePenalty|Game.UpdatePenalties|Test that when the boat moves outside of the lane that a penalty is given.|Start the game on any difficulty and deliberately move the boat outside of the lane then move back and stay in the lane for the rest of the race.|D key to move outside the lane. A key to move back into lane.|When the race ends, the player’s penalties should be for how long they were outside the lane|The player’s penalties were 58.645824|Pass|https://youtu.be/fdcYlq8d6LQ |Ayyesha
|11|PodiumScreen |UI.GameOverUI|To test the game displays a podium screen after the final race.|Complete the game on any difficulty to see if the podium screen is displayed at the end|n/a|Podium screen is displayed with the final scores|Podium screen was displayed with the final scores|Pass|https://youtu.be/_eI9i5FbZc8 |Ayyesha
|12|Fatigue|Game|To test whether the stamina bar of the player goes down over time.|Play the game on any difficulty, check to see that as the player moves, the stamina bar decreases|n/a|Stamina bar decreases as the player moves |Stamina bar decreased as the player moved|Pass|https://youtu.be/cQFQ-yjt4e8 |Ayyesha
|13|Robustness|Game.render|To test whether the game registers when robustness goes below 0.|Run the game and deliberately collide with as many obstacles as possible|Collide with as many obstacles|Game ends when player’s robustness goes below 0|Game ended when player’s robustness went below 0|Pass|https://youtu.be/cQFQ-yjt4e8 |Ayyesha
|14|ToolsBonus|Game.render|To test that colliding with a tool bonus causes the player’s boat robustness to increase|Play the game on easy difficulty (more bonuses spawn on easy mode) and select any boat. Collide with a tool bonus and see if the boat’s robustness increases|n/a|Boat’s robustness will increase|Boat’s robustness increased|Pass|https://youtu.be/THZiB5qQq98 |Ayyesha
|15|LightningBonus|Game.render|To test that colliding with a lightning bonus causes the player’s stamina to increase|Play the game on easy difficulty and select any boat. Collide with a lightning bonus and see if the player’s stamina increases|n/a|The player’s stamina will increase|The player’s stamina increased|Pass|https://youtu.be/XpUEvlCOA9E |Ayyesha
|16|Wheel Bonus|Game.render|To test that colliding with a wheel bonus improves the boat’s maneuverability|Play the game on easy difficulty, and select any  boat. Then collide with a wheel bonus and see if the boat is easier to maneuver |n/a|The boat will become easier to maneuver|The boat became easier to maneuver|Pass|https://youtu.be/UZc7iJFQ-oU |Ayyesha
|17|DrinkBonus|Game.render|To test that colliding with a drink bonus provides an immediate speed increase|Play the game on easy difficulty, and select any boat. Then collide with a drink bonus and see if the boat gets a speed boost|n/a|The boat will get a speed boost|The boat got a speed boost|Pass|https://youtu.be/y0ARDMSyfXY |Ayyesha
|18|WindBonus|Game.render|To test that colliding with a wind bonus increases the player’s acceleration |Play the game on easy difficulty, and select any boat. Then collide with a wind bonus and see if the boat accelerates faster|n/a|The boat’s acceleration increases|The boat’s acceleration increased|Pass|https://youtu.be/DEP9x3xaXHQ |Ayyesha
