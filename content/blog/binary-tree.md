+++
title="Binary trees"
date=2024-02-20
draft=false
[taxonomies]
tags=["uwaterloo-2a"]
+++

_Binary trees_ fall under the category of _directed acyclic graphs_.

{% definition(ref="Directed acyclic graph") %}
A graph consisting of vertices and edges, with each edge _directed_ from one vertex to another, such that following these directions will never form a _closed loop_.
{% end %}


# Binary trees

## Types

- A _full_ binary tree is a tree where every node has either 0 or 2 children.
- A _perfect_ binary tree has all interior nodes with two children and all leaves at the same depth or level.
- A _complete_ binary tree has every level filled, which can be efficiently represented using an array.

# AVL Trees

An AVL (Adelson-Velskii and Landis) tree is a binary search tree (BST) with a _balance condition_.
The condition ensures that the depth of the tree is $\mathcal{O}(\log N)$.
It should be easy to maintain.

A BST is an AVL tree if for every node, the height of the left and right subtrees differ by 1 at most.
Each node keeps track of its height.
The height of an AVL tree in practice is therefore always close to $log N$.

> The minimum number of nodes, $S(h)$, in an AVL tree of height $h$ is given by
>
> $$S(h) = S(h-1) + S(h-2) + 1$$

The properties of AVL trees guarantee $\mathcal{O}(\log N)$ tree operations.
The consequence is that we must perform _balancing_ of the tree to ensure it is still AVL.
Balancing is done using operations called _rotations_.

{% mermaid(height=200, caption="An AVL tree") %}
graph TD;
    5((5)) --> 2((2))
    5 --> 8((8))
    2 --> 1((1))
    2 --> 4((4))
    4 --> 3((3))
    8 --> 7((7))
{% end %}


## Balancing the tree

After insertion, only nodes on the path from the insertion point to the root may have altered balance.
This is because only these nodes have their subtrees altered.
As we follow the path up to the root and update the balancing information, we may find a node whose new balance violates the AVL condition.
Rebalancing the tree at the first such node going up (deepest) node guarantees the entire tree satisfies the AVL properties.

If the node to be rebalanced is $\alpha$, there are four cases why:

- We insert into the left subtree of ...
    - the left child of $\alpha$ (1)
    - the right child of $\alpha$ (2)
- We insert into the right subtree of ...
    - the left child of $\alpha$ (3)
    - the right child of $\alpha$ (4)

If the insertion occurs on the "outside," options 1 or 4, then a single rotation is needed.

{% example(ref="AVL tree in C") %}
Node declaration:

```c
struct AvlNode {
    int value;

    struct AvlNode *left;
    struct AvlNode *right;
    int height;
};


int avl_height(AvlNode *t)
{
    return (t == nullptr ? -1 : t->height);
}


void avl_insert(int value, AvlNode **root)
{
    if (*root == NULL) {
        *root = malloc(sizeof(AvlNode));
        (*root)->value = value;
        (*root)->left = NULL;
        (*root)->right = NULL;
        (*root)->height = 0;
    } else if (value < (*root)->value) {
        avl_insert(value, &((*root)->left));
    } else if (value > (*root)->value) {
        avl_insert(value, &((*root)->right));
    }

    avl_balance(root);
}


#define ALLOWED_IMB 1


int avl_max_height(AvlNode *a, AvlNode *b)
{
    int a_h = avl_height(a);
    int b_h = avl_height(b);

    return (a_h > b_h) ? a_h : b_h;
}


void avl_balance(AvlNode **root)
{
    if (*root == nullptr) {
        return;
    }

    if (avl_height((*root)->left) - avl_height((*root)->right) > ALLOWED_IMB) {
        if (avl_height((*root)->left->left) >= avl_height((*root)->left->right)) {
            avl_rotate_left(root);
        } else {
            avl_double_left(root);
        }
    } else if (avl_height((*root)->right) - avl_height((*root)->left) > ALLOWED_IMB) {
        if (avl_height((*root)->right->right) >= avl_height((*root)->right->left)) {
            avl_rotate_right(root);
        } else {
            avl_double_right(root);
        }
    }

    (*root)->height = avl_max_height((*root)->left, (*root)->right) + 1;
}


void avl_rotate_left(AvlNode **root)
{
    AvlNode *left = (*root)->left;
    (*root)->left = left->right;
    left->right = (*root);
    (*root)->height = avl_max_height((*root)->left, (*root)->right) + 1;
    (*left)->height = avl_max_height((*root)->left, (*root)) + 1;
    root = left;
}


void avl_rotate_right(AvlNode **root)
{
    AvlNode *right = (*root)->right;
    (*root)->right = right->left;
    right->left = (*root);
    (*root)->height = avl_max_height((*root)->left, (*root)->right) + 1;
    (*left)->height = avl_max_height((*root)->right, (*root)) + 1;
    root = right;
}


void avl_double_left(AvlNode **root)
{
    avl_rotate_right(&((*root)->left));
    avl_rotate_left(root);
}


void avl_double_right(AvlNode **root)
{
    avl_rotate_left(&((*root)->right));
    avl_rotate_right(root);
}
```
{% end %}

# Red-black trees

Red-black trees are "loosely balanced" trees.
They guarantee a maximum path traversal complexity of $\mathcal{O}(\log{n})$.
The advantage is in they can be balanced from root down instead of bottom up.

Red-black trees follow four rules:

1. Every node is either marked "red" or "black"
2. The root node is black.
3. If a node is red, its children must be black.
4. Every path from root to a leaf ("null") must have the same number of black nodes.

These rules work because the longest path is therefore at most two times the length of the shortest path.

Not all red-black trees obey AVL rules.
Red-black trees can be more lopsided.


## Insertion

The basic principle is we always add nodes as red, where they are supposed to be added in a normal BST.
Then we _rotate_ and _recolour_.

We rotate wherever we have two red nodes in a row.
This is done using the same procedure as in an AVL tree except we also change colour such that the new root is black and the old root is red.
A double rotation is also the same.
The new root is black and the old root is red.

Further: when we encounter a black node with 2 red children.
Re-colour the black node to red.
Re-colour the red nodes to black.
This preserves the black count down the paths.

# References

[^Pfaff]: Ben Pfaff, _GNU libavl_, Published 2022-01-03, [[Online]](https://adtinfo.org)
