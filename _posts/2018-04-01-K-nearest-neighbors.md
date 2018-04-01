---
title: Simple K nearest neighbor
author: Yuki
layout: post
categories: machine-learning
---

This is my first classifier that I coded: the simple K nearest neighbor algorithm.

Please reference this video for more detail: https://www.youtube.com/watch?v=AoeEHqVSNOw

```
class ScrappyKNN
```
This is the simple K nearest neighbor classifier class.

{% gist f7b2a32486e97926af978f11d8d917fb %}




- Logic

Please imagine a x and y coordinate graph with bunch of training points.

We are trying to classify if a point fits to group A or group B.

This K nearest neighbor algorithm take distance between the point we trying to determine and K number of points that are the closest to the point.

For this simple tutorial, K is 1 because we are just getting the closest point and assume the closest point's label is the answer.


The core of this simple algorithm is to get the closest points.

```
def closest(self, row):
        best_dist = distance.euclidean(row, self.X_train[0])
        best_index = 0
        for i in range(1, len(self.X_train)):
            dist = distance.euclidean(row, self.X_train[i])
            if dist < best_dist:
                best_dist = dist
                best_index = i
        return self.y_train[best_index]
```

euclidean distance is square root of (X2 - X1)^2 + (Y2 - Y1)^2 + (Z2 - Z1) .... however many features we have.

What was the accuracy ?

```
0.9666666666666667
```

Even the simple K nearest neighbor was able to predict in relatively high chance.

So again, I used Iris dataset. For Iris dataset, please take a look at decision tree with iris dataset blog => [decision tree with Iris data set]({% post_url 2018-04-01-decision-tree-iris-dataset %})