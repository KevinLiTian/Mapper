# Overview & Demonstration
In the second year of Electrical & Computer Engineering at the University of Toronto St.George campus, ECE297 is a course that's very similar to software engineering projects in the industry.This course aims for students to learn collaborative coding with Git and also be more proficient in c++ programming. The project of this course is a mapping software.<br/>

With the assistance by my teammates Xingyu (Ariel) Song <xingyu.song@mail.utoronto.ca> and Daixin (Ali) Tian <daixin.tian@mail.utoronto.ca>, I completed this project with a super usable and responsive mapping software using C++. Here are some main features of the mapper.<br/>

## Moving
Our mapping software supports zoom-in and zoom-out using either the mouse wheel or the "Zoom In" and "Zoom Out" buttons on the right side of the mapper. Users can also move the map by either dragging the mouse or using the direction pad on the mapper.<br/>

The detailedness is automatically adjusted base on the zoom in level as we don't want to overwhelm the users with clustered information when the map is zoomed out.
##### Video Demo
https://user-images.githubusercontent.com/99038613/169093331-e83db4a9-8a5e-410e-ac05-a502495b2027.mp4

## Night Mode
Night mode is also supported. We designed two set of colours, one for day mode and another for night mode.
##### Video Demo
https://user-images.githubusercontent.com/99038613/169098568-a00f306b-70b1-4836-b72f-032a91f4dc2a.mp4

## Search Bar
We implemented a search bar for the mapping software. There are two street name entries, if none or one of them is entered and searched, there will be a gentle reminder message in the bottem left corner. The search bar supports partial street name entries such as "Yon" for "Yonge" and also auto adjust regardless of upper or lower cases such as "bLoor" for "Bloor". It also ignores spaces before or in the middle of the street names such as "  Bl  oor" for "Bloor".<br/>

Once two street names are entered and searched, the intersection of two streets will be highlighted with an highlighting icon and the map will automatically adjust to a level that is comfortable for users to look at the intersection and its surroundings.<br/>
##### Video Demo
https://user-images.githubusercontent.com/99038613/169096278-cec04515-f38d-49dd-beca-ec04168759d5.mp4

## Feature & Point of Interests
Our mapper also shows feature names and also point of interests names with icons. Point of interests are certain types of buildings and infrastructures including restaurants, libraries, hospitals, banks, etc.
##### Video Demo
https://user-images.githubusercontent.com/99038613/169092699-345dbdb1-0e81-4b54-95c9-31a41c227cc9.mp4

## Language Support
Since the users can have any cultural backgrounds, we added in some language supports for Mandarin, Japanese, Persian, etc. 
##### Video Demo
https://user-images.githubusercontent.com/99038613/169098466-60d5fced-64b7-4a03-aaee-1b0557c22d9a.mp4

## Multi-City Support
Our map supports a number cities for instance Toronto, Canada as default, New York, USA, Beijing, China, etc.
##### Video Demo
https://user-images.githubusercontent.com/99038613/169098545-ec594927-7f52-44b7-8f63-d69b0ee93001.mp4

## Pathfinding
Pathfinding feature is also included in our mapping software. The users can select two intersections on the map and use the nagigate path button to find a guaranteed shortest path between the two intersections. We also have a animation for the direction of travelling. The users can reverse the path, and reverse it again; they can clear the path, or clear everything using the clear highlights button.<br/>

We started with Dijkstra's algorithm and then adding some heuristics to improve it to A Star Algorithm.
Visualizations of the two algorithms are demonstrated below.<br/>
##### Video Demo
https://user-images.githubusercontent.com/99038613/169098618-429099d9-8448-4f19-92ca-eb0dcb4b9844.mp4

##### Dijkstra's Algorithm
https://user-images.githubusercontent.com/99038613/169098940-589cd8ad-b0d4-4f67-8f97-eedfbb09b2b1.mp4

##### A Star Algorithm
https://user-images.githubusercontent.com/99038613/169098982-1b5642c2-1f71-46a4-9345-3a5eafbe2f8e.mp4

## Travelling Courier
This part is solely algorithm so there's no video demo. In the previous part, pathfinding, there's only one starting intersection and one destination intersection. But what if there's a lot of starting points and destinations? For example, a courier can start at any truck depot in the city and go to pickup package 1 then go to drop off package 1. What if there's hundreds of pickups and drop offs?<br/>

This is a variant of the Travelling Salesman Problem (TSP) which is a computationally hard (NP) problem, we cannnot compute all the possibilities and find the best one. Therefore we designed a customized algorithm to try to find the best route. We did a precomputation using multi-destination Dijkstra's algorithm to compute the travel time between each of the two interested points (depot/pickup/dropoff). Then use the greedy algorithm as a starting point, using random optimization techniques such as 2-opt to improve the route. We intended to use simulated annealing but it was close to the deadline so we did not include it. <br/>

Route (Unit in average travel time):
> Random: ~400000 sec <br/>
> Greedy: ~100000 sec <br/>
> Optimized: ~92000 sec <br/>

## Contribution
| Team Member    | Line Inserted   | Line Deleted   | Numbers of Commits   |
| :-------------:| :-------------: | :------------: | :------------------: |
| Tian Li        |     20514       |     10830      |            104       |
| Daixin Tian    |      6978       |     662        |            83        |
| Xingyu Song    |      3995       |     1588       |            102       |

- Stats taken from Git

## Conclusion
This project teaches me and my teammates a lot. Not only how to code more efficiently, how to improve code style and commenting, but also how to communicate ideas and coding collaboratively. Moreover, it teaches us to start early and not to procrastinate. After completing the project, my teammates and I felt so proud of ourselves as it is such a big project for us at the time. In fact, this is the first actually project in our lives. <br/>

Though there was things we could've done better, I am truly satisfied and happy for what we've done and grateful for my teammates. Happy coding!

## Contact ME
If you are interested in the source code or the original documentations, please do contact me through my email <kevintian.li@mail.utoronto.ca> or <kevin.li20021106@gmail.com>. You have to prove that you are not a current ECE297 student since this will be an academic integrity issue. If you are, try to think and code it yourself as it will be a great practice to improve your software engineering skills; though if you have any questions, feel free to share it with me!
