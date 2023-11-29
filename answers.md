## CS 520 In-class exercise 4

By Patrick Walsh, Matthew Lips

Due **December 6th, 11:59pm**

---

## Questions


### Question 1

**Question**

For the [Synoptic build](https://github.com/ModelInference/synoptic), identify 2 design principles or
best programming practices that are satisfied. For each design principle or best practice satisfied,
illustrate with an example from the build.

**Answer**

### Question 2

**Question**

Briefly explain how you added the tracing statements to the first version of the RowGameApp (Step 1
above).

**Answer**


### Question 3

**Question**

Briefly explain your technique for sampling the traces of the first version of the RowGameApp (Step 2
above). This explanation should include how you decided to stop sampling.

**Answer**

### Question 4

**Question**

For your inferred model of the first version of the RowGameApp, briefly describe one expected
behavior. Briefly describe one unexpected behavior.

**Answer**

### Question 5

**Question**

Was it easier to add the tracing statements to the second version of the RowGameApp (Step 1 above).
Why or why not?

**Answer**

It is easier to add the tracing statements in the second version of RowGameApp because of the MVC architecture pattern. The first version does not have any organization, so finding the parts in the code where you should put the "uses", "manipulates", and "updates" logs is tedious. However, in the second version of the game there is the model which clearly organizes where to put the "manipulates" logs, the view which clearly organizes where to put the "updates" logs, and the controller which clearly organizes where to put the "uses" logs.

### Question 6

**Question**

Your inferred model of the second version of the RowGameApp should be the MVC architecture
pattern. Did you need to change your technique for sampling the traces of the RowGameApp (Step 2
above) to produce that inferred model? Briefly explain why or why not.

**Answer**

I should not have to change the sampling technique for the traces of the RowGameApp because the game should have the same behavior and functionality regardless of the architecture pattern behind the scenes. In both versions I should be able to perform all of the actions in the game including playing, wining, losing, making a tie, and resetting. All of these actions should be sampled in both cases to attempt an exhaustive search of the possible states of the game with both versions.

### Question 7

**Question**

Propose a semi-automated of fully automated technique for sampling the traces of the RowGameApp
(Step 2 above).

**Answer**

A fully automated technique for sampling traces of the RowGameApp would be to have a script that randomly perform actions allowed by the program by calling its controller functions. In this context it would choose randomly and programmatically click any of the grid options, the reset button, or terminate the game. This could be run through many times since it is automated by the computer and so many of the possible states will be found within the samples, and much faster than a human.

### Question 8

**Question**

What is the primary disadvantage of any such trace sampling technique?

**Answer**

The primary disadvantage of this trace sampling technique is that it is unlikely to find the edge cases within the program. Humans have the intuition to find possible states in the game that can result in problems. But for an automated process it will be unlikely that an automated program can find this result searching randomly, especially if it requires multiple steps. So, an automated system could find many more states than a human, but it could fail in searching for rare or unique states among the large possibilities.

### Question 9

**Question**

Propose one technique for illustrating the differences between two inferred models (represented as
FSAs).

**Answer**

FSAs allow you to see the different states of the program and the transitions between those states. One technique for illustrating the differences is to compare the different states and their multiplicity. For example with the rowGameApp-arch.pdf it has the INITIAL state, two manipulates states, a uses state, an update state, and a TERMINAL state. We can see that the manipulates has two states because the program initializes the model in the game before going into the MVC pattern illustrated by the uses, manipulates, updates cycle where it could be manipulated again. Looking at the types of states and multiplicity allows one to see the structure of the program flow and see how it may compare to another program with a different architecture.

### Question 10

**Question**

What is one use case where model inference would be helpful to the developers?

**Answer**

The model inference can be especially helpful to the developer if they encounter a transition that is possible within the program they have not considered. As a program grows it may be complicated as to what the possible actions a user can take at any point, and so laying out the program in a finite state machine can show the developers a clear guide to see what is allowed. This can allow developers to see where potential problems for bugs may arise in the program and make debugging more efficient.