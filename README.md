A* Program writeup
 
(10 pts) High-Level Description of A* code:
Our A* code as it is working now by taking the megaminx that we generated from the first assignment. The megaminx is made using arrays of arrays so our A* code works by having two definitions, one that checks how many pieces are misplaced and the other definition that tests the viability of each move. A* first checks to see if MegaMinx is already solved if it is already solved it sends a message and exits the code. If it is not already solved the definition that tests each move works by rotating face 0, calls the function count_misplaced_stickers which counts the amount of misplaced stickers, and stores that variable and face that was turned to give the least amount of misplaced stickers. The face is then turned counterclockwise to undo the move and then face 1 is tested the same way. The amount of misplaced pieces calculated from turning face 1 is then compared to the previous low of misplaced pieces and the lowest is chosen. This process is done for each face 0-11. Once every face has been tested it then performs a clockwise move on the face that produced the least amount of misplaced places. This process is repeated until count_misplaced stickers returns a value of 0 and once that happens it finishes checking the rest of the faces and turns the corresponding face thus solving the megaminx. That is a basic rundown of how our A* program works. This setup, although it works sometimes, is not what our group was aiming for. We can successfully run k = 5 times but that was as far as we were able to go. After k = 5 times the program will fail a majority of the time and will be stuck in an endless loop. It can get stuck in an endless loop at lower k values but it happens much less often compared to k =5 and k = 6. We thought this heuristic would work because we planned on the number of misplaced pieces being somewhat linear for each increasing k value but we found out that our thoughts about the megaminx were wrong. This is where we began to implement a 3D array instead of a 2D array so we could add weight to misplaced pieces depending on their distance. We wanted to implement a new heuristic, which we have stated below, but were unable to due to the way we set up our data structure. 
 
(10 pts) Admissible Heuristic:
The heuristic that we implemented and realized was not admissible was finding the total number of displaced pieces. We then began to come up with a new heuristic which we were unable to implement. The heuristic that we wanted to use involves the Manhattan Distance Formula. The Manhattan distance is a formula that calculates the sum of the distance of each piece from its goal destination. For this project though we would have to divide that number 15 since 15 stickers are displaced from a single move. This heuristic is admissible because it does not overestimate the number of moves to solve the Megaminx. This heuristic, if implemented correctly, would of allowed us to implement a successful solver for the MegaMinx
 
(10 pts) Description of data structures:
 The data structure that we used for our Megaminx was a homogeneous data structure because we used nested arrays. We began with an array of an array to make a 2D Megaminx but realized that we would need to make it an array of an array of an array to make it a 3D object so we could calculate the distance of the pieces. We successfully implemented the 3D array but commented the code out because it would not allow our previous 2D code to work but still wanted to show an attempt and leave the code for future work we may want to work on.
 
(40 pts) A* Code / State Representation / Child Function / Add h and G Functions / Use Heap/Priority Queue Correctly and Appropriately: The link to the GitHub that has the code can be found here https://github.com/chriscahill88/MegaMinxSolver/blob/main/MegaMinxSolver

 The state representation in our code is the array of an array of an array, that is true because this setup of an array of arrays allows us to capture our configuration. 
The Child function would be in the solve definition, lines 856-864, this is because it iterates through every possible state from the current state.
To check for the solved state before applying the child function is done by the while loop which will not run the code unless there are misplaced pieces and thus will stop the code if it already solved.
We were not able to implement an H and G function because we were unable to calculate the Manhattan distance correctly.
The heap and queue were also not able to be implemented because of us not being able to implement the Manhattan distance

 
(15 pts) Graphs:
  
This is our graph of the average number of misplaced stickers compared to which move we were on in the solving process. Our graph only goes to five since that is where our algorithm fails after k =5. These values are the average of five runs.
 
Our graph is linear for K in relation to the number of nodes retrieved from the search tree since each time it goes a layer deeper it creates 12 new nodes and does not continue any farther on previous nodes. There may be confusion on our end as to whether it should be the sum of the total nodes, which we have above, or if it should be just the number of new nodes which means we would’ve had a horizontal line at 12 for each k value.
 
(8 pts) Learning Outcome:
 I learned from this assignment how important it is to have the correct data structure for your project. We spent some time talking about what data structure we wanted to use for this project thinking about the ease it would bring for the first assignment but failed to look forward toward this project which ultimately was a very bad decision. This is because our data structure is very difficult to calculate the Manhattan Distance and we were unable to correctly calculate it. I also learned a lot about algorithms and how much better they can be compared to coding every single possibility. My first thought for this project was that we would have to implement thousands of if-else statements for each individual piece but once the idea of using an algorithm came to mind and we had one that might have worked I realized how much time and effort it would save. I also learned the value of an admissible heuristic. We spent a good amount of time implementing a heuristic that was not admissible and although all that time was not fully wasted, we did spend a decent amount of time on something that did not live up to the expectations of what we hoped and for the description of the project.
 
(7 pts) Who-did-what: (in comments of submission)
 
 
 

![image](https://github.com/chriscahill88/MegaMinxSolver/assets/43705092/002f9f1a-6738-4ec0-a070-4fb97ea80bf4)
