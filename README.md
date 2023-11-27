

Abstract:	This paper presents algorithms for identifying the largest possible group of binary vectors such that the distance between any two distinct vectors is at least a certain value. We accomplish this by creating a graph, called the Hamming graph, where each vertex represents a vector and two vertices are connected by an edge if the distance between their corresponding vectors is greater than or equal to the specified value. 10
 


1.	Introduction	
In this project, we will be addressing a problem in coding theory related to the Hamming distance between binary vectors. The Hamming distance between two vectors is defined as the number of indices at which the two vectors differ. Given a set of binary vectors, the goal is to find the maximum number of vectors that can be chosen such that the Hamming distance between any two distinct vectors is at least a certain value "d". This maximum number is referred to as A(n, d).

One way to approach this problem is to construct the Hamming graph, which is a graph with 2^n vertices given by binary strings of length n. There is an edge between two vertices in the graph if the Hamming distance between the corresponding binary vectors is greater than or equal to "d". The size of a maximal clique in this graph will be equal to A(n, d).
 
The task at hand is to implement efficient algorithms to compute the maximal clique in the Hamming graph. It is important to note that the problem of finding a maximal clique is NP-hard, so our algorithms will need to be as efficient as possible.	8


2.	Materials and Methods
Language
C++
Libraries and Algorithms	
Boost Graph: The Boost Graph Library (BGL) is a C++ library that provides algorithms to help with creating and organizing graphs. It offers a range of pre-implemented algorithms and tools for customizing graph data structures. The BGL is designed to be generic and works with a wide range of graph data structures, and it provides algorithms for common graph tasks such as searching, sorting, and traversing. It is a useful tool for C++ programmers working with graphs. 

Unordered_set: An unordered set is a type of data structure used by the Bron-Kerbosch algorithm to store cliques (sets of connected vertices) discovered during the search. In order to keep track of the vertices that have been taken into account during the search and to make sure that each vertex is only taken into account once, the vecS and undirectedS templates are used to store undirected vertices in a vector or an unordered set, respectively. The vecS and undirectedS templates allow for effective insertion and removal as well as quick membership testing, whereas the unordered set provides quick insertion and removal of elements without the need to maintain order.

Vector: The vector library is a collection of classes and functions that allow you to create and manipulate vectors. Vectors are sequence containers that store elements in a contiguous block of memory, and they can be resized dynamically as needed. To use the vector library, you will need to include the "vector" header in your program and then create a vector object by using the "vector" class template and specifying the type of element you want to store. You can then use various member functions and operators of the vector class to manipulate the vector, such as adding elements, accessing elements at a specific index, and getting the number of elements in the vector.

Born-Kerbosch: The Bron-Kerbosch algorithm is an efficient method for finding cliques (groups of vertices all connected to each other) in an undirected graph. It does this by considering each vertex in turn, checking whether it can be added to the current clique, and then repeating the process on the remaining vertices if it can. It is useful for a variety of applications.

Clique-visitor: The Bron-Kerbosch algorithm uses a function called a clique-visitor to process each clique (a group of connected vertices) found during the search. The current clique is passed to it as an argument, and it is in charge of updating the clique variable and carrying out any necessary operations on the clique. As the algorithm searches the graph for cliques, it is called repeatedly. The Bron-Kerbosch algorithm can be easily modified thanks to the clique-visitor.

ItoB: The function converts an integer "x" into a binary vector of a specified length "n" by first initializing an empty vector "v" and adding the least significant bits of "x" to it in a loop. The binary representation of "x" is then padded with zeros until it reaches the desired length "n." The function then reverses the order of the elements in the vector so that the most significant bit is at the front. The resulting binary vector is returned.

 HammingD: This is a function that calculates the Hamming distance between two binary vectors. The Hamming distance is defined as the number of indices at which the corresponding elements of the two vectors are different. The function takes two constant references to std::vector<int> as arguments and returns the Hamming distance between them. If the vectors have different lengths, the function returns -1 to indicate an error. Otherwise, it calculates the distance by iterating over the elements of the vectors and counting the number of indices at which they are different.

HammingG: This is a header that constructs a Hamming graph, which is a graph with vertices given by binary strings of a specified length "n" and edges connecting pairs of vertices that have a Hamming distance of at least "d". The function takes two arguments: "n" is the length of the binary strings, and "d" is the minimum required Hamming distance. It returns a Graph struct consisting of an unordered_set representing the adjacency list of the graph and an integer representing the number of vertices. The function creates the graph by iterating over all pairs of vertices and connecting them with an edge if their Hamming distance is greater than or equal to "d".
 
 
