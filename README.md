Copyright @Profeanu Ioana & Iordache Madalina Gabriela

Rope Data Structure in C
-------------------------------------------------------------------------------
Implementation:
    A rope is a data structure composed of smaller strings that are used to 
efficiently store and manipulate a very long string. For example, a text
editing program may use a rope to represent the text being edited, so that
operations such as insertion, deletion, and random access can be done
efficiently.
-------------------------------------------------------------------------------
Mandatory functions implemented:

1. concat: concatenate two ropes(rt1, rt2) into a single rope
    - We create a new root node with left = rt1->root and and right = rt2->root
    - The weight of the new root will be equal to the length of the left child
    - It forms a new rope string by merging two initial ones


2. indexRope: return the character located at position i
    - To return the character at given position i, we begin a recursive search
from the root node using the findChar function 
    - We follow the premise that if the weight of the current node is lower
than the value of i, we subtract the weight from i and move right. If the
weight is less than the value of i we simply move left. We continue till the
point we reach is a leaf node.
    - Allocate memory for the character at position i and call the recursive
function to traverse the rope tree in order to find the requested element.


3. search: return the string between two given points
    - Get the size of the searched substring and allocate memory for it 
    - Traverse the interval [start, end) in a for loop and call indexRope 
function to recursive search through the tree for the character at specific
position in the given interval
    - Store the returned characters in an array of strings and return the final
substring


4. split: split the string into two new strings
    - Split function based on recursive travel through the nodes until reaching
the character with the given index
    - The left splitted tree's root will always be the initial tree's root
    - The right spliited tree will be obtained by concatenating its right and
left sides
    - If we travel to the right, we either cut the link to the root's right and
the right splitted tree will be the right subtree of the initial tree (this
happens when the root's weight is equal to the index), or we continue
travelling down on the right side
    - If we travel to the left, we look for orphan nodes and create the split
nodes pair; if we have two orphan nodes, we merge them together and the right
side of the split nodes pair will be the merged nodes
    - If we reach the leaf, we check again for orphan nodes; then we concate-
nate the components of the right split subtree depending on the number of
orphan nodes, then get the final two splitted trees
    - At the end, update the weight of the result trees and end the recursive
search


5. insert: insert string at given position
    - Insert function can be done with a split and two concats
    - Split the string at the given index and create two subtrees, left and
right, then create a new node and tree for the node to be inserted
    - Concatenate the left subtree with the new tree, and then concatenate the
result with the right subtree
    - The result will be a new tree which contains the inserted string


6. delete: delete string between two given points
    - Delete function can be done with two splits and one concat
    - There are three cases: 
        - if the length of the string is shorter than the sum of start
    and len:
            - if the start is shorter than the string length, split the rope
        from start and return the left subtree
            - if the start is longer than the string length, return the entire
        rope
        - else, split the rope from start and from start + len; concatenate
    the left side of the first split with the right side of the second
    split and return the result
-------------------------------------------------------------------------------  
