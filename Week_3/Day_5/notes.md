# w3 - d5
* [teacher notes](https://github.com/Eric-Lombardo/lectures-2020-mtl-feb03/tree/master/w2d3)

## apps and app data
* apps are all about data. you can delete an app's code but if the data is still there and safe an app can be recoded to access that secure data
* but if you deelte data than the app has nothing to fetch/dispaly and it's useless
* liek fi you delete facebook's code all the pics/likes are stored in the DB, but if you delete all the data in DB then facebook becomes useles and will display nothing

## trees
* each circle in a tree is called a node
* all connections between nodes are called edges
* a node represents a key entity and contains data about that entity

![diagram of a tree](https://i.imgur.com/0DLZ1jI.png)
* the node at the very top of a tree is called the root node and nodes at the very bottom are called leaf nodes
* every node except for the root node has a <strong>single</strong> parent
* every node that isn't a leaf node ahs 1 or more <strong>children</strong> nodes
* all children with the same parent node are called <strong>siblings</strong>

## requirements of trees
* we can build a tree out of anything as long as the nodes have a single parent and as many children. example:
  1. node (any employee)
  2. parent (boss)
  3. children (subordinates)
  4. data (name, salary, title of that node)
* it's all about relationships that determine if a tree structure is good idea for this collection of data

## traversing a tree
* traversing through a tree's nodes is similar to looping through items of an array
* breath first traveral:
  1. start with the root node
  2. then move onto roots children
  3. then move onto those nodes children
  * basically level by level top - down
  ![breath first](https://github.com/Eric-Lombardo/lighthouse-web-notes/blob/master/docs/20200222_115608.jpg?raw=true)
* depth first traversal:
  1. starts at the root node and chooses left or right and goes all the way down to a leaf node then goes back to parent and takes the next path
  ![depth first](https://github.com/Eric-Lombardo/lighthouse-web-notes/blob/master/docs/20200222_115614.jpg?raw=true)
* breath and depth are the two most common ways to traverse a tree

## subtrees
* sub trees are just zoomed-in trees of a particular node
* every node is a "root" node of a subtree
* even a leaf node is a "root" node of a sub tree with zero children
![subtrees](https://github.com/Eric-Lombardo/lighthouse-web-notes/blob/master/docs/20200222_120552.jpg?raw=true)