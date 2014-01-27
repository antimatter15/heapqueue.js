# Heapqueue.JS

This implementation is very loosely based off js-priority-queue
by Adam Hooper from https://github.com/adamhooper/js-priority-queue

The js-priority-queue implementation seemed a teensy bit bloated
with its require.js dependency and multiple storage strategies
when all but one were strongly discouraged. So here is a kind of 
condensed version of the functionality with only the features that
I particularly needed. 


## Usage

Using it is pretty simple, you just create an instance of HeapQueue
while optionally specifying a comparator as the argument:

    var heapq = new HeapQueue()

    var customq = new HeapQueue(function(a, b){
    	// if b > a, return negative
    	// means that it spits out the smallest item first
      return a - b
    })

Note that in this case, the default comparator is identical to
the comparator which is used explicitly in the second queue.

Once you've initialized the heapqueue, you can plop some new
elements into the queue with the push method (vaguely reminiscent
of typical javascript arays)

    heapq.push(42);
    heapq.push("kitten");

The push method returns the new number of elements of the queue.

You can push anything you'd like onto the queue, so long as your
comparator function is capable of handling it. The default 
comparator is really stupid so it won't be able to handle anything
other than an number by default.

You can preview the smallest item by using peek.

    heapq.push(-9999)
    heapq.peek() ==> -9999

The useful complement to to the push method is the pop method, 
which returns the smallest item and then removes it from the
queue.

    heapq.push(1)
    heapq.push(2)
    heapq.push(3)
    heapq.pop() ==> 1
    heapq.pop() ==> 2
    heapq.pop() ==> 3

## Licensing

Like js-priority-queue, I hereby release the source code for this
project into the Public Domain. That said, it'd be pretty neat to 
know what this gets used for, if anything.