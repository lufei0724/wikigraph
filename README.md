# Wikigraph

##Introduction
An algorithm to compute the distance between wikipedia articles.
But what is the distance between two pages? We can consider each Wikipedia article (represented by its id) to be a node, of the graph. The links from one page to another one can be interpreted as the edges of this directed graph. Therefore the distance between page A and page B is the number of links that a user needs to click on to reach page B from page A.

##BFS Algorithm recap
The skeleton of the recursive method iter is provided to you. To fill in the rest, remember that BFS iteration first explores all the neighbors of a node and after that, it moves on to the neighbors of each neighbor.

To do so the algorithm relies on a set of visited nodes to remember which nodes where already explored and therefore avoid being stuck in infinite loops around graph cycles (for example A -> B -> C -> A). It also maintains a (priority) queue which contains the nodes to visit next. In this case, we modified this queue to contain not only the ID of the next nodes to analyze, but also the distance of the node from the start of the search. Finally, the implementation of breadthFirstSearch in this assignment also receives a maxDepth argument which describes the threshold to respect for the exploration.

The algorithm proceeds as follows:

- When no node is left to visit or when we exceed maxDepth, the search is considered failed and completes with a None

- Otherwise, we retrieve the next node to visit (and its distance from the start of the search) and its neighbors. If the destination is amongst the neighbors, our search is complete, and we can return the distance. Otherwise, we add the neighbors to the queue with the associated distance and we perform a recursive call.

##Download the dataset
To be able to test your code without Internet access, we have assembled for you a small dataset. This small graph contains all the pages that are at distance 2 from the Scala (programming language) article. The dataset might be incorrect or out of date and should be used only for testing.

You can download the file from here

Please put the file inside a directory named enwiki-dataset, in the project root directory. The path to the dataset (relative to the project root directory) should be enwiki-dataset/smallwiki.db so that it matches the filename used in src/main/resources/application.conf.

