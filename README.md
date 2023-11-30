# PageRank Example in Python 3.9

This is a simple implementation of the PageRank algorithm in Python.

# Usage
Adjust variables
<li>`damping_factor` - the damping factor (residual probability of a random page visit); default is 0.85
<li>`epsilon` - the convergence threshold for L1 norm; default is 0.000001
<li>`max_iterations` - the maximum number of iterations; default is 100
<li>M - the adjacency matrix representing the web graph; choose from provided examples or create your own

<br>Create the adjacency matrix M by creating a square matrix of size $n_Xn$, where n is the number of nodes (pages) in the web graph. 
A non-zero value $i,j$ in a column entry represents the presence of an edge (link) from page $j$ to page $i$.
Each row must sum to 1 (it must be row-stochastic). In addition, there must be all zeros on the main diagonal (a page cannot link to itself). If a row has all zeros, then the row is replaced with a row of $1/n$, where n is the number of nodes (pages) in the web graph.

<br>For example, if page 1 has links to pages 2 and 3, then the column entry for page 1 would be [0.5, 0.5, 0]. If page 2 has links to pages 1, 3, and 4, then the column entry for page 2 would be [0.33, 0, 0.33, 0.33]. If page 3 has no links, then the column entry for page 3 would be [0, 0, 0, 0]. If page 4 has a link to page 1, then the column entry for page 4 would be [1, 0, 0, 0].
<br>To interpret the results, the index of the highest value in the resulting vector is the page with the highest rank.

For DiGraphs, the adjacency matrix is computed as follows:
<li>For each node, the probability of transitioning to another node is 1 / number of outgoing edges
<li>If a node has no outgoing edges, then the probability of transitioning to another node is 1 / number of nodes (due to the damping factor)
