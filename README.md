# KD-tree for search in periodical da

## Suitable for
This method is suitable only for those datasets, that are rarely modified as the preprocessing has quite big time complexity. At that cost, we are able to preform quite fast computation of nearest neighbours for high-dimenstional periodical data with use of the python KD-tree library. 

## Problem setting
In periodical data cannot be applied any of the standard metrics, that the sklearn.neighbours.KDTree implements (eucledean, minkowsky, manhattan, ...). 
Let us explain it on an example. Let our period by 360 and let us have an angle 10. Let some element of an vector in KD-tree have value of 350. Then by eucledian metrics the distance between 10 and 350 is 340 and this vector is propably not suitable candidate for the nearest neighbour. But the periodic distance is only 20, which makes the vector quite suitable candidate. 

The task is, for such a vector (with 350 as an element) to be recognized by KD-tree as a suitable candidate in the example case. 

## Purpouse
This concrete model was made for searching nearest neighbours in torsion angles of 12 dimensional biological data. First ten elements are periodical. The rest are nonperiodical. 

## Method
To make use of the python library sklearn.neighbours.KDTree, without modifying it, preprocessing of our data was needed. This modification can be made quite simply. We can just clone each vector in each dimension. Ex. for period = 360 we clone the angle 350 to -10. So that it computes the right distance. 
This way we obtain $2^n$ vectors, where n is the number of periodical dimensions of our vector. This number may sound huge, but keep in mind, that we make this computation only when the data set is changed. The search in KD-tree is preformed in $O(\log(m))$, where m is the size of the dataset. From this we see, that n is just an additive constant by preforming the search of nearest neighbours.

We build the tree from numpy array by each run as our data set is not so large (ca. 41 000 vectors). It is also possible to store the KD-tree on disc. 



