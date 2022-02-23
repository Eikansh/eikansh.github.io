---
layout : note
title : "Design and Analysis of Algorithms"
tags : notes 
modified_date : 2020-10-11
---

## Lecture 1 : Divide & conquer : convex Hull, median finding 

### Convex Hull

#### Convex hull problem
Given $$n$$ points in plane $$S=\{(x_i, y_i) \vert i=1,2,\ldots,n\}$$ assume no two have same $$x$$ coordinates, no two have same $$y$$ coordinates, no three in a line.  
Convex Hull is a smallest convex polygon containing all points in $$S$$, denoted as $$CH(S)$$.  

$$CH(S)$$ is represented as Sequence of points on the boundary in clockwise order as a doubly linked list 

#### Brute force algorithm
Draw a line connecting two points, if all the points are on one side of it, it is a segment of convex hull.
Complexity : $$O(n^3)$$   
$$O(n^2)$$ segments  
$$O(n)$$ test complexity, so a overall $$O(n^3)$$ complexity.

#### Divide & conquer algorithm
Given a problem of size n, divide it into "$$a$$" subproblem of size $$n/b, n>1$$  

Sort the points by $$x$$ coordinates (once for all)
For input set $$S$$
- Divide into left half $$A$$ &right half $$B$$ by $$x$$ coordinates
- Compute $$CH(A)$$ & $$CH(B)$$ recursively
- Combine


#### Merging
Why it can't be trivial algorithm while merging two convex subhulls?  
[Reason](https://youtu.be/EzeYI7p9MjU?t=1982)  
##### Two finger algorithm 
This algorithm is used to find points to merge two convex subhulls.  
Time complexity : $$\Theta (n)$$  
- Choose closest point in both subhulls which are closest to the axis
- Draw a line connecting both points. This line will intersect on axis at $$Y_{ij}$$
- Move counter clockwise in left hull and clockwise in right hull
- Check whether $$Y_{ij}$$ increased or not. If it decreased, discard them and continue while loop ends.  
{% highlight c %}
i=1
j=1
while(y(i, j+1) > y(i, j) or y(i-1, j) > y(i, j))
	if y(i, j+1) > y(i, j)
		j = j+1 (mod q)
	else 
		i = i-1 (mod p)
return (a_i, b_i)as upper tangent
{% endhighlight %}

##### Cut & Paste
Used to remove lines and merge convex subhulls connecting points found using Two finger algorithm.  
Time complexity : $$\Theta (n)$$
- Find upper tangent $$(a_i, b_j)$$ and lower tangent $$(a_k, b_m)$$.
- First link $$a_i \to b_j$$
- Go down the $$b$$ list till you see $$b_m$$, link to $$a_k$$
- Continue till you return to $$a_i$$   

##### Time Complexity
Time complexity for general case,  
$$
\begin{align}
T(n) = 2T(n/2) + \Theta(n) \\
\implies \Theta(nlogn)
\end{align}
$$  
$$n/2$$ because we can divide subproblems into roughly two halves

### Median Finding

[Median Finding Notes](https://www.cs.cornell.edu/courses/cs2110/2009su/Lectures/examples/MedianFinding.pdf)

Given a set of $$n$$ numbers, define $$rank(X)$$ as the numbers in the set that are $$\leq X$$  
$$Rank(X)$$ : Position of element $$X$$ in the sorted array.
Lower median : element of rank $$\left \lfloor{(n+1)/2}\right \rfloor$$  
Upper median : element of rank $$\left \lceil{(n+1)/2}\right \rceil$$  

$$Select(X, i)$$, $$i$$ is the rank
- Pick $$x \in S$$
- Compute $$k=rank(x)$$, and generate two subarrays B and C such that, $$B=\{y \in S \vert y < x\}$$, $$C=\{y \in S \vert y > x\}$$

{% highlight c %}
if k == i
  return x
else if k > i
  return Select(B, i)
else if k < i
  return Select(C, i-k)
{% endhighlight %}

Pick $$X$$ cleverly  
- Arrange $$S$$ into columns of size $$5$$ ($$\left \lceil{n/5}\right \rceil$$ columns)
- Sort each column (big elements on top) in linear time
- Find "median of medians"

How many elements are guaranteed to be $$> X$$?  
Half of the $$\left \lceil{n/5}\right \rceil$$ group contribute at least 3 elements $$>X$$ except for 1 group with less than 5 elements & 1 group that contains $$X$$.  
So, if we exclude these two columns, there are :  
Atleast $$3(\left \lceil{n/10}\right \rceil - 2)$$ elements $$>X$$  
Atleast $$3(\left \lceil{n/10}\right \rceil - 2)$$ elements $$<X$$  

##### Reccurence

Time complexity : $$O(n)$$    

$$T(n) = O(1)$$ for $$n \leq 140$$  
$$T(n) = T(\left \lceil{n/5}\right \rceil) + T(\left \lceil{7n/10+6}\right \rceil) + \Theta (n)$$  
- $$140$$ is a arbitrary constant. It can be any constant value.
- Term $$T(\left \lceil{n/5}\right \rceil)$$ is for finding median of medians or pivot. $$\Theta(1)$$ time for dividing and sorting array for $$\left \lceil{n/5}\right \rceil$$ columns.
- $$T(\left \lceil{7n/10+6}\right \rceil)$$ is the max size of partition that can be recurred on.
- $$\Theta(n)$$ is the time taken to partitioning the array w.r.t. pivot.
