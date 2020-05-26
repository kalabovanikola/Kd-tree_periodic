# KD-tree for search in periodical data

## Suitable for
This method is suitable only for dataset, that is rarely modified as the preprocessing has quite big time complexity. At that cost, we are able to preform quite fast computation of nearest neighbours for high-dimenstional periodical data with use of the python KD-tree library. 

## Method
To make use of the python library sklearn.neighbours.KDTree, preprocessing of our data was needed. 

## Purpouse
This concrete model was made for searching nearest neighbours in torsion angles of 12 dimensional biological data. First ten elements are periodical. The rest are nonperiodical. 

