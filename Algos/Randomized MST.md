### Definition
Def: let G = (V, E) connected, undirected, weighted
* w: E -> R
* 
![[Pasted image 20230323211413.png]]
* Assume all weights are different (distinct)
* WANT: T = (V, E_t) subtraph of G such that 
	* T is a tree ( connected and cycle -free)
	* T spans all vertices (i.e. number of edges = V - 1)
	* w(T) = $\sum_{e \in T}{w(e)}$ is minimal among all such trees

### Determinisitic MST algo
* 1920's [[Boruvka]]'s alg O(E log(V))
	* clusters of vertices and take shortest btw each clusters
		* start with set V and E_t = null
		* for ech vertex v, let e_v = $\argmin_{v \in e}{w(e)}$
		* repeat until E_t = V - 
		*
#### Kruskal's Alg  O(E log(V))
1. Sort edges by weight
2. start adding edges to MST

1. for i=1 to m:
	1. if E_tU{e_i} is cycle-free:
		1. E<- E_tU{e_i}

Makes use of union/find

#### Prim's Alg  O(E log(V))
1. pick a vertex v add the lightest edge e_v to E_t
2. add to V(E_t) the lightest edge in the boundary
3. priority queue

### Randomized Design

#### Properties
##### Cut Property
![[Pasted image 20230323214850.png]]
Need to use one of the edges in the cut
* Let G = V, E be a connected weighted grpah. Let L, R be a cut of V, then the edge of the min weight in the cut belongs to the MST

##### Cycle Property
Let G = V, E be a connected weighted graph. Let c be a cycle of G -> the heaviest edge in c is not in the MST
* no mater how you do the cut of the cycle there will always be a better way to connect two vertices without the heaviest vertex

##### Conclusion
Def: let g = V, E and let T be a forest of G. An edgge e is said to be T = good if:
1. T union e is cycle-free
2. T U e has cycles but e is not the heaviest edge of the cycle

Let T be a sub-forest of the MST
-> the MST is a subset of T U { all T-good edges}

Let T be the MST ->
{all T-good edges} = T

#### KKT 
* run 3 round sof [[Boruvka]]'s alg to get G' = V', E'
* randomization: E_1 subset E' by picking each edge in E' uniformly at random
	* if see heads keep vs tails throw away -> G_1 = (V', E_1)
		* may drop connectivity -> forest
	* keep half n^2 -> n^2 / 2
* Recursively call design on the new generated graph
	* T_1 = KKT(G_1)  
		* n^2 /2 -> n
	*  G_1 = (V', E_1)
* E_2 = {all T_1-good edges in E'}
	* go back through all the E' edges to see if the E_1 edges are good (those that are should be kept)
	* recover good edges
* T_2 = KKT(G_2 = (V, E_2))
* return T_2 U {edges from Boruvka's}

##### Remarks
* after Boruvka |V|  <= n/8, |E'| <= m 
	* times 1/2 after every iteration
* randomized $E(|E_1|) = |E'| / 2 <= m/2$

**Lemma:** E(|E_2|) <= 2|V'| = n / 4
* we build T_1 as follows:
	* sort according to weights of E' (accending)
	* flip a coin every time kruskals alg wants to add an edge to the MST
		* if the coin is heads -> keep in MST
		* 