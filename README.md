# Djikstra's Implementation in real-world application_Verilog
This project focuses on implementation of Djikistra's Algorithm using Verilog

Dijkstra's algorithm is a crucial tool in graph theory and computer science, with broad applications
in areas such as route planning and network optimization. The project
delves into the algorithm's core concepts, emphasizing its capacity to find
optimal paths while managing computational complexity. By providing a
step-by-step analysis of algorithm execution and demonstrating its
practical application through a real-world scenario, this project aims to
equip individuals and organizations with the knowledge and tools
necessary to leverage Dijkstra's algorithm for improved
Navigation and resource allocation.




# Introduction

The Dijkstra algorithm, a fundamental technique in graph theory for
finding the shortest path between two points, has widespread
applications in various fields. Its utility extends to hardware designs,
making it pertinent to explore its implementation using Verilog.
Integrating the Dijkstra algorithm into Verilog facilitates its
utilization in specific scenarios where the constraint of identifying
the shortest path is crucial.

Implementing Dijkstra's algorithm in Verilog opens avenues for
optimization tailored to particular hardware platforms. This
customization holds the potential to enhance the overall algorithm
performance and reduce power consumption when compared to
executing the algorithm on a conventional, general-purpose
processor. Thus, this project endeavors to harness the capabilities of
Verilog to efficiently implement Dijkstra's algorithm, offering a
hardware-centric solution for scenarios demanding optimal
pathfinding and resource utilization.

# Step-by-Step Implementation for the Project:

 Step  1. Initialization:
Set the distance of the starting node to 0, and the distances of
all other nodes to infinity.
Add the starting node to a map1, where the priority is based on the
distance from the starting node.

 Step  2. Loop:
For each neighbor of the node, calculate the distance to the neighbor
by adding the distance from the current node and the weight of the edge
between the two nodes.
If the new distance to the neighbor is smaller than its current distance,
update the neighbor’s distance. We consider the node with the shortest
path length after updating with respect to the present node and select this
node as the next node.

 Step  3. Termination:
The algorithm terminates when the destination node is reached.

 Step  4. Path Reconstruction:
The shortest path between the starting node and the destination
node can be reconstructed by following the previous nodes from the
destination node to the starting node.

# Verilog Code Explanation

The Verilog code takes in a clock signal, start signal, start node,
end node, and outputs a final path and a done signal.

The state register is used to keep track of the current state of the
algorithm. The map1 and map2 arrays are to store the current distance
from the start node to each node and the previous node in the shortest
path to each node respectively.

The visit and visited registers are used to keep track of which nodes
have been visited and which nodes have been fully explored.
The w array is used to store the weight of the edges between nodes.
The “cal” function is used to calculate the distance to neighbouring
nodes and update the map1 and map2 arrays.

The final_temp register is used to temporarily store the final path. The
count register is used to keep track of which index of the final_temp
register is being written to.

This code implements a finite state machine for the path planning
algorithm. The state machine has four states, which are explained
below:

# State Assignment

State 0:
This is the initial state of the state machine. It waits for the start
signal to be asserted. When the start signal is detected, it transitions
to state 1.

State 1:
In this state, the map is initialized, and the starting node is marked
as visited. Then, the state machine transitions to state 2.

State 2:
In this state, the algorithm performs path planning by iteratively
selecting the unvisited node with the lowest tentative cost, and
updating the costs of its neighboring nodes. Once all nodes have
been visited, the state machine transitions to state 3.

State 3:
This state is responsible for backtracking from the goal node to the
start node, and generate the final path. It starts by setting the current
node to the goal node, and then iteratively adding the previous node in
the path until the start node is reached.

The implementation uses an adjacency matrix to represent the graph,
and the costs of the edges are stored in a two- dimensional array.
The algorithm keeps track of the tentative cost of each node, which is
the cost of the path from the start node to the current node, and the
previous node in the path, which is used for backtracking.
Once the goal node is reached, the algorithm backtracks from the goal
node to the start node to generate the final path.
The final path is stored in the final_path output signal, which is a
concatenation of the node indices in the path.
