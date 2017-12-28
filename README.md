# Friends Recommendation System
Friends Recommendation System using MapReduce
(Note - I also used a Hadoop FS to deal with large data storage, so the mapping operations wont work on a local machine)

There is a very common data set used for this project, the `soc-LiveJournal1Adj`. It essentially contains a file with a number that represents a person, and the people he/she are friends with, i.e other numbers that are linked to the person. These links are bi-directional.

The goal of the system is to make a recommendation to a user U such that they have a large number of friends in common. The output criteria is-
* recommend a maximum of n=10 users
* the recommended list should be in descending order of most common friends, ie, if the (u,x1) has more common friends than (u,x2) then the   list should display in the form {x1,x2.....}

### Requirements
* Hadoop or any other cluster FS

### Code
Compile the file like you normally would on a file system, then run with-
`hadoop jar Recommendation.jar Recommendation <input dir> <output dir>`
  
The results will be displayed on the screen itself, but this can be changed to be saved into a file quite easily.

{NOTE - I've used tool runner to parse command lines arguments and run the map-reduce in a cohesive manner. The mapper maps the program to separate lists of users and user friends, and passes it to the reducer. To handle inconsistencies, I've used the Comparator class within my Reducer.}

An example of the output for some of the links would be - 

9021    {9020, 9016, 9017, 9022, 317, 9023}
9993    {9991, 13134, 13877, 13478, 34299, 37941, 34485, 34642}
8941    {8943, 8944, 8940}
9020    {9021, 9016, 9017, 9022, 317, 9023}


