# Overview
The work during the semester is being divided into 4 milestones 1 written document (WD) and 2 oral presentations (OP). The milestones are written mainly in the libstreetmap/src directory. <br/>

Here's the overview and insight in a software engineering perspective of the milestones and a quick summary of the content in each of the source code files, and also a brief explanation on the written document and the two oral presentations.

## M1 - Efficient APIs
> “There is more to life than increasing its speed." –Mahatma Gandhi

An efficient application programming interface (API) is essential for a successful software engineering project, it makes developments easier and improve the responsiveness of the application.<br/>

In the first milestone, we were to use the two lower-level APIs (StreetDatabaseAPI and OSMDatabaseAPI) written by the course staff to form a higher-level API. The course staff provided us with the header files of the two lower-level APIs and a header file for M1 (m1.h). This content is written in m1.cpp <br/>

##### m1.cpp
In this source code file, we implemented all the precomputations and any preperation for later use. Datas are pre-loaded into data structures for faster look-ups. Some useful functions are written for later uses such as finding travel time of certain street, common intersection between certain streets, etc. There are two core achievements:

* Fast: A good API should allow the application to look things up or do things faster, we achived this by loading data into proper data structures and having as low time complexity as possible (O(1) in most cases)

* Error Free: We also passed all the test cases including private ones, more extreme and "corner", set by the course staff aiming to test exaustively to make sure our high-level API has no problem at all

## M2 - Visualizing an Interactive Map
> “The real voyage of discovery consists not in seeking new landscapes, but in having new eyes." –Marcel Proust

The users are seeking for an interactive graphics interface, and this milestone provides them with one. In M2, we designed and implemented the graphics user interface (GUI) for our mapping software. The course staff provided us with the "EZGL" library and also with the gtk library, also a header file for M2 (m2.h). <br/>

Main features are listed in the README.md in the parent directory. This milestone is not that difficult regarding the coding part but takes lots of work and design not only the code style but also the aesthetics of our map such as colour sets and shape design. The content is in m2.cpp <br/>

##### m2.cpp
In this source code file, we implemented everything you can see on the map, all the visuals are coded in this file. The main features again are listed in the README.md of the parent directory. There are two core achievements:

* Fast Redraw Speed (frame per sec): The essential part of an interactive GUI is that is should respond to user input as quick as possible. We made it happen by smart uses of data structures and good code design. The average redraw speed is ~0.03sec which corresponds to ~30fps, looks smooth in human eyes. 

* Aesthetics: Users like pretty GUIs. That's why we dig deep into designing by searching through design websites and assessed some existing colour sets, and finally came up with the current design of our GUI. The main frame is set by the course staff but we modified the buttons, the texts and also adding in the drop-down menu. The colour sets are also adjusted through several commits. Our design earned almost full mark in aesthetic part of the milestone. Though "There are a thousand Hamlets in a thousand people's eyes." We still believe that our design looks comfortable for most people.

## M3 - Pathfinding and Directions
> “If you don’t know where you are going, you’ll end up someplace else.” – Yogi Berra <br/>
> “If you don’t know where you’re going, any road will take you there." – Lewis Carroll

Shortest path finding is a typical algorithmic problem, and also commonly used in mappers. In this milestone, we were to implement a pathfinding feature that finds a guarenteed shortest path between the two user selected intersections on the map and also shows the visualization of the path. The demo video is in the parent directory.<br/>

There were two options, the Dijkstra's algorithm and the A* algorithm. We started with the Dijkstra's algorithm as our baseline and added in some heuristics based on the estimated future travel time to improve it to the A* algorithm. Note that both the Dijkstra's and A* are not exactly the same as some examples online, we wrote it so it suits our mapping software. The content is in m3.cpp

##### m3.cpp
In this source code file, we implemented the path finding algorithm and some related helper functions to find the shortest path such as a traceback function and a compute time function. In the algorithm, we used a priority_queue with a custom comparator to constantly search for neighbouring intersections until we find the destination. The core achievements are:

* Fast: The users needs an interactive map with fast responses, so we provide them with a super fast pathfinding feature. Since we are using A* and the algorithm is designed flawlessly, the search speed is fast (under 0.1sec) which seems instant to human eyes.

* Error Free: We passed all tests even some extremely rare cases that can occur on maps since our algorithm considered all of them and handled them perfectly. 

## M4 - Traveling Courier
> “A person who never made a mistake never tried anything new.” –Albert Einstein

In the previous milestone, pathfinding, there's only one starting intersection and one destination intersection. But what if there's a lot of starting points and destinations? For example, a courier can start at any truck depot in the city and go to pickup package 1 then go to drop off package 1. What if there's hundreds of pickups and drop offs?<br/>

This is a variant of the Travelling Salesman Problem (TSP) which is a computationally hard (NP) problem, we cannnot compute all the possibilities and find the best one. Therefore we designed a customized algorithm to try to find the best route. We did a precomputation using multi-destination Dijkstra's algorithm to compute the travel time between each of the two interested points (depot/pickup/dropoff). Then use the greedy algorithm as a starting point, using random optimization techniques such as 2-opt to improve the route. We intended to use simulated annealing but it was close to the deadline so we did not include it. <br/>

We utilized multi-threading using the openMP library in some independnet for loops to speed up the process. By doing this, we are able to test more random local changes to get better routes.

##### m4.cpp
In this source code file, we implemented a high-level function and several functions it calls such as precomputation, greedy algorithm and optimization.<br/> 

The precomputation is using a variant of M3 Dijkstra's algorithm, changing the termination condition from one destination to multiple destination. Store it to a 2D vector for faster look-ups.<br/>

Our greedy algorithm is an advanced version of the traditional greedy algorithm thanks to my teammate Daixin Tian. He proposed that if we "look forward" instead of being so greedy and only looking at the next step, there's a higher chance to get a better route. <br/>

The optimization method is proposed by Tian Li combining several random optimization methods for a higher chance of a better solution. Since everything is random, there are some parameters need to be adjusted. Thanks to my teammate Xingyu Song, tested lots of combinations and recorded them with an Excel spread sheet, making our optimization more efficient. Here's some result routes:

Route (Unit in average travel time):
> Random: ~400000 sec <br/>
> Greedy: ~100000 sec <br/>
> Optimized: ~92000 sec <br/>

### Note
m1-4_helpers.h are some header files to help declaring custom functions/data structures and define constants for corresponding milestones<br/>

structs.h is a header file containing all of the useful structs for all the milestones, which struct is used for which source file and what functionality if clearly indicated by thhe commenting in the header file

## Written Document
The written document is written one week before M2 as a proposal to what we will be implementing in the GUI. We spent a whole week doing researches and writing drafts, and editing. Our proposal was one of the best proposals among the entire course. Thanks to our Communication Instructor (CI) Lucas Wilson, giving us opinions patiently. We improved our professional writing skills a lot as engineers.

## Oral Presentation 1
This presentation was after the first two milestones, when we had our high-level API and the basic GUI ready for demonstration. We introduced to our CI what we achived and why are they useful for users. 
- Link to slides: https://docs.google.com/presentation/d/17uaVGfswNP8pdmIhD9UwKfx8kp-AMXZtYMQTvJ3Rp-Q/edit?usp=sharing


## Oral Presentation 2
This presentation was after all four milestones, as a final examination, when we completed our project. We introduced not only what did we do, but also how did we achieve them, both the technical/coding side and in a non-technical perspective.
- Link to slides: https://docs.google.com/presentation/d/12W4h1JvxGXaRVg4Kg-x0Qi6BOFLAstiPD4dy4iKiv30/edit?usp=sharing

## If You are Interested
If you are interested in the original copies of the handouts (Milestones, WD, OPs) and our WD or the source codes, please contact me using emails in the README.md of the parent directory
