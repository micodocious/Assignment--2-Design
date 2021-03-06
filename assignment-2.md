# Assignment 2 (design)
Mico Santiago

## Based on what we know about linked lists, stacks, and queues, design a queue data structure

### 1.	 What functions are we likely to need for a queue to function like the one discussed in class?	
The queue we talked in class was LIFO or last in first out, like in a queue of cars at a toll, a care enter from the back and the first car in front leaves, therefore insertion performed at one end and deletion can be performed at the other. Functions would include
		
	-	A operation that means to insert an item into the back of the queue. (Push/enqueue)
	-	A operation that removes the front item. (Pop/dequeue)
	-	A operation that tells us the whats in the front.
	-	A operation that tells us it is empty. 
### 2.  What values will we need to know about the structure for our queue to function properly?
Using the functions above, we implement a queue with an array. In an array implementation, we have the front and the rear. Now lets say we want to insert a number in int A[10]. By inserting a 5 in the rear, we push out the number in the front. Therefore,
	
	int A[10]
	front <- -1
	rear <- -1
	empty() 
	{
		if front ==-1 && rear ==-1				//by setting front and rear to -1 we declare the queue is empty
			return true
		else
			return false
	}
	push(x)
	{
		if empty()
			return
		else if empty()
		{
			front <- rear <- 0
		}
		else 
		{
			rear <- rear + 1
		}
		A[rear] <- x
	}
	pop()
	{
		if empty()
			return
		else if front == rear
			front <- rear <- -1
		else 
			front <- front +1
	}
	front()
	{
		return A[front]
	}
The problem with this psuedocode, is that we cannot keep push numbers into the array anymore because the variables 0 and 1 cannot be used again, but we can make the array into a "circle" and after 9 we go to 0. 

## Based on what we know about linked lists, design a list data structure that allows us to add (insert) or remove (delete) values at a given location in the list (instead of the top of a stack or the front or back of a queue):
### 1. What functions are we likely to need for a list to function like this?
-	Insert a value at a given postion
	
		head = NULL; //empty list
		insert(2,1); //List: 2
		insert(3,2); //List: 2,3
		insert(4,1); //List 4,2,3
		insert(5,2); //List 4,5,2,3

-	delete a linked list  node at nth position
		
		Our list is 4,5,2,3
		delete(1); //List: 4,2,3
		Our list is 4,2,3
		delete(0); //List: 2,3
### 2. What values will we need to know about the structure for our list to function properly?
insert()
-	When you create a new node, the newly created node will have link field set to the link field of the n-1 node. example is we have a list(address[value, next address]) of [head|200] -> 200[2|100] ->100[4|250] -> 250[6|0] ->NULL	We will create a new node with value 8 at 3rd position, therefore we will set 150[8|250] and breaking the link between 100[4|250] -> 250[6|0]. Thus, [head|200] -> 200[2|100] ->100[4|150] -> 150[8|250] ->250 [6|0] ->NULL

delete()
-	First we fix the links so the node is not part of the list. for example we want to remove node 3 or position 3 in our list here: [head|200] -> 200[2|100] ->100[4|150] -> 150[8|250] ->250 [6|0] ->NULL. So instead we will have [head|200] -> 200[2|100] ->100[4|250]  ->250 [6|0] ->NULL	Notice node 3 is gone, and node 2 address points to node 4 now.
-	We have now explicitly deallocate the space that was taken by the node. 
