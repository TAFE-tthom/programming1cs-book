# Supplementary - Trees

**This Section Is Currently a WIP**

While I have reserved this chapter for another series, it is best that some idea that more than lists exist.

## What are trees?

In computer science, a tree is an abstract model of a hierarchical structure:

– A tree consists of nodes with a parent-child relation
– if n is parent of m, then m is a child of n
– a node has at most ONE parent in a tree
– a node can have zero, one or more children

Linked lists and trees share the concept of a `Node`. However, the implementation of a `Node` for a tree is one where there is usually mroe than one link instead of single one.

## Properties and Terms With Trees

Trees will have more going on, similar to a linked list, there exists the idea of a `root` node. There are `Ancestors` and `Descendants` of a particular node.

Common terms with trees:

* Root: Node without a parent
* Ancestors of a node: itself, parent, grandparent
* Descendant of a node: Itself, any child, any grandchild.
* Subtree: Tree consisting of a node and a its descendants, typically
    a tree that is inside a tree.


We can also extract properties of a tree such as the `Depth`, `Level` and `Height`.

* Depth of a tree, number of ancestors not including itself
* Level of a tree, The set of nodes with a given depth
* Height of a tree, maximm depth of any node


## Traversals

As a generalisation, there exist two kinds of traversals on with trees.

* Preorder Traversal
* Postorder Traversal

However, with special kinds of trees such as a `Binary Tree`, there exists the idea of an **In-Order Traversal**.

### Pre-Order Traversal

Let's examine what a Pre-Order Traversal looks like.

```
preOrder(node) {

    visit(node)

    foreach child in node.children {
        preOrder(child)
    }

}
```

*Hang on!? Why is PreOrder calling itself?*

We have a recursive function, it can be an elegant way to demonstrate an algorithm however whenever you see a recursive function, the proper implementation will likely substitute a `Queue` or `Stack` instead.


### Post-Order Traversal

```
postOrder(node) {

    foreach child in node.children {
        postOrder(child)
    }

    visit(node)
}
```

There isn't much of a change, the main focus here is we are visiting the children first and then visiting the current node.



## Binary Trees

While we have talked about trees generally, we will focus on a special version of a tree. A Binary Tree.

A binary tree is where a node within a tree only has two children.

* Left Node
* Right Node

We can apply the same traversal function for pre-order or post-order traversal.However, we can also apply **in-order traversals** with this particular tree variant.


### In-Order Traversal

A particular traversal method we can apply here is an `inOrder` traversal.

```
inOrder(node) {

    if (node.left != null) {
        inOrder(node.left);
    }
    
    visit(node)
    
    if (node.right != null) {
        inOrder(node.right);
    }
}
```

You should *consider the similarity with binary search* as you may gain a reasonable of insight between this traversal when transformed into a search and binary search.
 
