# BatchHL

<!-- This is the implementation of the paper "BatchHL-Answering Distance Queries on Batch-Dynamic Networks at scale", currently under review in SIGMOD. -->

The format of the dataset text file is as follows: <br/>
Line 1 : |V| |E| <br/>
Line 2 : vertex_u deg_u v1 ... vn, where v1 to vn are neighbors of u. Note that the vertex id are from 0 to (V-1), where V is the number of vertices. There are no self loops in the graph, i.e., no edge from any vertex to itself. 

To see the accepted format for datasets, batch updates and query pairs, you may refer to the Sample folder. After the test inputs are ready, please us the following commands to test BatchHL.

=====================================

#1 - Compile source files using the following command:<br/>
g++ -O3 -std=c++11 -pthread main.cpp -o run

=====================================

#2 - Construct Labelling:<br/>
./run construct_labelling @1 @2 @3<br/>
@1: name of the dataset<br/>
@2: number of landmarks<br/>
@3: file to store labelling

Example:<br/>
./index construct_labelling graph.txt 20 graph_labelling

=====================================

#3 - Update Labelling:<br/>
./run update_labelling @1 @2 @3 @4 @5 @6<br/>
@1: name of the dataset<br/>
@2: number of landmarks<br/>
@3: file to load the labelling from<br/>
@4: batch file containing updates<br/>
@5: method parameter (0 to run BHL+ or 1 to run BHL)<br/>
@6: parallelism parameter (0 to parallelize, otherwise 1)

Example:<br/>
./index update_labelling graph.txt 20 graph_labelling batch.txt 0 0

=====================================

#4 - Perform distance queries<br/>
./run query-dis @1 @2 @3 @4 @5<br/>
@1: name of the dataset<br/>
@2: number of landmarks<br/>
@3: file to load the labelling from<br/>
@4: file containing query pairs<br/>
@5: file to write query results<br/>

Example:<br/>
./index query_labelling graph.txt 20 graph_labelling query_pairs.txt query_results.txt









