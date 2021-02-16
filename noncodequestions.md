1. Draw a BST
Given the data 3,1,4,6,9,2,5,7, if you were to insert this into an empty binary search tree, what would the tree look like? (Draw the tree, no coding needed here.)
Draw the BST with the keys - E A S Y Q U E S T I O N

         3
       1   4
        2   6
           5 9
            7   

      E
    A          S
              Q          Y
            E           U
             I         S
              O         T
            N

2. Remove the root
Show how the above trees would look like if you deleted the root of each tree. (Draw the trees, no coding needed here.)

        2
      1    4
             6
            5  9
              7

      A
               S
              Q          Y
            E           U
             I         S
              O         T
            N

     
3. on bst.js

4. What does this program do?
Without running this code in your code editor, explain what the following program does. Show with an example the result of executing this program. What is the runtime of this algorithm?

function tree(t){
    if(!t){
        return 0;
    }
    return tree(t.left) + t.value + tree(t.right)
}

I believe it prints out the binary search tree. It has a run time of O(log n);

5. Height of a BST
Write an algorithm to find the height of a binary search tree. What is the time complexity of your algorithm?

function height(t) {
  if(!t) {
    return -1;
  }

  const lHeight = height(t.left);
  const rHeight = height(t.right);

  if(lHeight > rHeight) {
    return lHeight + 1;
  } else {
    return rHeight + 1;
  }

}

the runtime of this algorithm is O(n);

6. Is it a BST?
Write an algorithm to check whether an arbitrary binary tree is a binary search tree, assuming the tree does not contain duplicates.

function isBST(t) {
  if(t.left === null && t.right === null) {
    return true;
  }
  else if (t.left > t || t.right < t) {
    return false
  }
  else if (!t.left) {
    return isBST(t.right)
  }
  else if (!t.right) {
    return isBST(t.left)
  }
  return (isBST(t.left) && isBST(t.right));
}

This has to be O(n) because it goes through the entire tree

7. 3rd largest node
Write an algorithm to find the 3rd largest node in a binary search tree.

function 3rdLargest(t) {
  curr = t.root;
  3rdLargest = Null;

  count = 0;

  while (curr) {
    if(!curr.right) {
      count += 1;
      if (count === 3) {
        3rdLargest = curr;
      }
      curr = curr.left;
    }
  }
}