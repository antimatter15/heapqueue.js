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


## Blog Post

I have a habit of writing blog posts in sublime text in lieu of legitimate readmes. This project was simple and short enough that I think I did manage to write something with a passable semblance to a functional readme before initiating this quest to craft a blog post. 

This is hardly a project that I'd expect to go down in the annals of my blog as particularly interesting or notable. Instead, it's a rather boring low-level computer sciencey thingy who would feel perfectly comfortable amidst homework assignments.

In fact it's virtually assured that documenting this endeavor, the combination of writing the words which comprise this post and the documentation already written on how to use this rather simple library will inevitably consume more of my time than actual coding (people who are more familiar with highly intricate professional software tapestries may claim that in fact the ideal and typical state is as such). 

Notice that I've managed to spend three paragraphs (well, my paragraphs are on the order of two sentences, so it doesn't even qualify for the fourth-grade definition for what a paragraph is) talking about the uninteresting character of the project, its relative dimunitive size, and the process of writing about the subject, without actually describing what exactly the project is. I could spin this as some kind of diversion, that knowing what exactly this thing even did probably wouldn't lend "much amaze" or even a modest "such wow". 

It is a binary heap priority queue, a teensy bit shy of 50 lines, a mere kilobyte minified. It's very loosely based off of Adam Hooper's js-priority-queue but considerably smaller. 

Now that I've gotten the actual informative and useful part of the blog post off our shoulders, I can take you along for the unproductive plunge into the rather lame backstory for the project. I was working on a port of the Telea inpainting algorithm and needed a priority queue, because the little incremental insertion sort that I hacked together in two lines was taking far longer than was acceptable. 

With my considerable Google-Fu, I searched "javascript heap queue" and found js-priority-queue as well as PriorityQueue.js (https://github.com/STRd6/priority_queue/tree/master). They both happened to be implemented in CoffeeScript, which I love, except not really. I like the syntax, but creating a project using it usually involves setting up some compilation pipeline in order to get it to do the things that I want it to do. Overall, it's a bit too much of a hassle for little projects. 

I couldn't actually find the source code for PriorityQueue.js so I settled for js-priority-queue. It was a bit annoying in that it required require.js to function and included several storage strategies that were totally useless. So I copied and pasted a few files together and stripped it of its AMD dependencies and created a somewhat dieted version. 

At that point, I was overcome by this undeniable urge. 


Inevitably the forces of not-invented-here syndrome strike again now
with redoubled fervor! Well I mean, when I’ve already hacked together
parts of js-priority-queue in order to satiate a moderate case of
software anorexia, I might as well go the step further to strip it down
to its bare necessities and write it the way I guess I would have
written it.


