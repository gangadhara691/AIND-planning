# Report Analysis a Planning Search For a Air Cargo 
This project implements deterministic logistics planning problems for an Air Cargo transport system using a planning search agent.Optimal plans for each problem are computed.
## Non-Heuristic  Search Strategies Analysis
For air_cargo_p1, air_cargo_p2, and air_cargo_p3, metrics on number of node expansions required, number of goal tests, time elapsed, and optimality of solution for each search algorithm are given in the tables below. Included the result of at least three of these searches, including breadth-first and depth-first and greedy best first graph search.
#### Solving Air Cargo Problem 1
|Search Type	|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|Breadth First Search |43 |56 |180 |6|0.0827|Yes|
|Depth First Graph Search|	21|	22|	84|	20|	0.0447|	No|
|Greedy_best_first_graph_search with h_1|7|9|28|6|0.01191|Yes|
#### Solving Air Cargo Problem 2
|Search Type	|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|Breadth First Search | 3343|4609|30509  |9|33.94|	Yes|
|Depth First Graph Search| 624|625| 5602|619|7.64|	No|
|Greedy_best_first_graph_search with h_1|998|1000|8982|21|5.7|No
#### Solving Air Cargo Problem 3
|Search Type|Expansions|Goal Tests|New Nodes|Length|Time (s)|Optimal|
|-----------|--------------|---------------------------------|
|Breadth First Search |14663|18098|129631|12|250.5|	Yes|
|Depth First Graph Search|408| 409|3364|392|4.17|	No|
|Greedy_best_first_graph_search with h_1|4031|4033|35794|22|31.6|No|


>### Analysis
>Non-heuristic search strategies used are 'breadth first search','greedy best first graph search', and 'depth first graph search'. Breadth first search always considers the shortest path first and a result of it finds a solution to the problem in a reasonable amount of time and in an optimal way.

>Depth first graph search finds a solution quickly and consumes little memory, but it the length is not optimal. It lacks optimal nature because it does not give priority or consider node over another, it simply explores the nodes that take it as deep as possible in the graph.

## Informed (Heuristic) Search Strategies Analysis

 A* planning searches using the heuristics are implemented on 'air_cargo_p1, air_cargo_p2 and air_cargo_p3'. Metrics on number of node expansions required, number of goal tests, time elapsed, and optimality of solution for each search algorithm are provided below.
 
#### Solving Air Cargo Problem 1
|Search Type|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|A* Search h_1|55|	57|	224	|6|	0.103|Yes|
|A* Search with h_ignore_preconditions|	41|43|170|6|0.101|Yes|
|A* Search h_pg_levelsum|11|13|50|6|2.91|Yes|
#### Solving Air Cargo Problem 2
|Search Type|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|A* Search h_1|4853|4855|44041|9|35.5|Yes|
|A* Search with h_ignore_preconditions|1450|1452|13303|9|12.85|Yes|
|A* Search h_pg_levelsum|86|88|841|9|249.6|Yes|
#### Solving Air Cargo Problem 3
|Search Type|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|A* Search h_1|17783|17785 |155920 |12|126.6|Yes|
|A* Search with h_ignore_preconditions|5003|5005|44586|12|43.44|Yes|
|A* Search h_pg_levelsum|311|313 |2863|12|1185.75(> 10 min)|No|


>### Analysis
>Heuristic searches performed well as the problem become more complex. This is more evident in the air cargo problem 3, where the “A* Search with ‘h_ignore_preconditions’” performance was optimal and the fastest amongst those that were optimal. The ‘h_pg_levelsum’ heuristic performed poorly because of the complex nature of heuristic.

## Comparing Non-Informed and Heuristic(Taken best from both)
#### Solving Air Cargo Problem 1
|Search Type	|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|Breadth First Search |43 |56 |180 |6|0.0827|Yes|
|A* Search with h_ignore_preconditions|	41|43|170|6|0.101|Yes|

#### Solving Air Cargo Problem 2
|Search Type	|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|Breadth First Search | 3343|4609|30509  |9|33.94|	Yes|
|A* Search with h_ignore_preconditions|1450|1452|13303|9|12.85|Yes|
#### Solving Air Cargo Problem 3
|Search Type|	Expansions|	Goal Tests|	New Nodes|	Length	|Time (s)|	Optimal|
|-----------|--------------|---------------------------------------------------------------|
|Breadth First Search |14663|18098|129631|12|250.5|	Yes|
|A* Search with h_ignore_preconditions|5003|5005|44586|12|43.44|Yes|


>According to the results obtained in this analysis, the breadth first search strategy can solve planning problems both fast and optimality, which makes it a good candidate to start off an analysis when dealing with search planning problems. As the complexity of the problems increase, it might be worth to consider if a heuristic based approach such as “A* Search with ‘h_ignore_preconditions’” can outperform breadth first search and thus be used instead.

## Optimal Sequence of Actions

### The following  describes an optimal sequence of actions to solve each of the air cargo problems provided  from the above tables:
|Problem	|Search Type	|Optimal Sequence of Actions|
|-----------------------------------------------------|
|Air Cargo Problem 1 |breadth_first_search |Load(C1, P1, SFO)<br/>Load(C2, P2, JFK)<br/>Fly(P2, JFK, SFO)<br/>Unload(C2, P2, SFO)<br/>Fly(P1, SFO, JFK)<br/>Unload(C1, P1, JFK)|
|Air Cargo Problem 2 | astar_search with h_ignore_preconditions|Load(C3, P3, ATL)<br/>Fly(P3, ATL, SFO)<br/>Unload(C3, P3,SFO)<br/>Load(C2, P2, JFK)<br/>Fly(P2, JFK, SFO)<br/>Unload(C2, P2, SFO)<br/>Load(C1, P1, SFO)<br/>Fly(P1, SFO, JFK)<br/>Unload(C1, P1, JFK)|
|Air Cargo Problem 3 |astar_search with h_ignore_preconditions|Load(C2, P2, JFK)<br/>Fly(P2, JFK, ORD)<br/>Load(C4, P2,ORD)<br/>Fly(P2, ORD, SFO)<br/>Unload(C4, P2, SFO)<br/>Load(C1, P1, SFO)<br/>Fly(P1, SFO, ATL)<br/>Load(C3, P1, ATL)<br/>Fly(P1, ATL, JFK)<br/>Unload(C3, P1, JFK)<br/>Unload(C2, P2, SFO)<br/>Unload(C1, P1, JFK)|

### References

1. Stuart J. Russell, Peter Norvig (2010), Artificial Intelligence: A Modern Approach (3rd Edition).






