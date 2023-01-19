# `%hw4`

Homework #4 for Hoon School Live.  
  
Urbit has several ways to represent and work with text values.  The list is broader than just a text representation format, however, and affords the most common way to work with data in Hoon.

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your ship, not your fakeship.)

##  Text in Hoon

There are four basic representations of text in Urbit:  cords, knots, terms, and tapes.

- Q1. Which text representation do each of the following values fall into?

  - `@t` cord
  - `@ta` knot
  - `@tas` term
  - `(list @t)` tape
  
  - `'nitwit'`
  - `~.blubber`
  - `%oddment`
  - `"tweek"`

- Q2. How would you convert the list `~[114 97 105 110 98 111 119 32 115 104 101 114 98 101 116]` to a `tape`?  (You should actually try this in Dojo to make sure your proposal works; it's similar to clearing a type by passing through the empty aura.)

- Q3. FizzBuzz is a classic computer science challenge question.  For this step, write a gate in an arm `++fizz` which accepts a count and counts upward from one to that value, appending the number each time OR "fizz" (as tape) every third number until the count is reached.  (I.e., given 7, it should yield the list ~[1 2 "fizz" 4 5 "fizz" 7].)  (Answer with the arm as the only arm in a regular |% core.)

- Q4.  For this step, write a gate in an arm ++buzz which accepts a count and counts upward from one to that value, appending the number each time OR "buzz" (as tape) every fifth number until the count is reached.  (I.e., given 7, it should yield the list ~[1 2 3 4 "buzz" 6 7].)  (Answer with the arm as the second arm after ++fizz in a regular |% core.)

- Q5. For this step, write a gate in an arm `++fizzbuzz` which accepts a count and counts upward from one to that value, appending the number each time, "fizz" every third number, and "buzz" every fifth number until the count is reached.  (I.e., given 15, the list should count from 1 to 15 thus: ~[1 2 "fizz" 4 "buzz" "fizz" 7 8 "fizz" "buzz" 11 "fizz" 13 14 "fizz buzz"].)  Make sure that it outputs *both* "fizz" and "buzz" for numbers that are divisible by both three and five.  (Answer with the arm as the third arm after `++fizz` and `++buzz` in a regular |% core.)  

- Q6. In the lesson, there was an exercise to produce a library and a generator which counted the number of words in a given tape.  Compose the library such that it consists of a `|%` barcen core including a `++split-tape` arm and a `++count-elements` arm.  Submit the library as your answer here.

- Q7. In the lesson, there was an exercise to produce a library and a generator which counted the number of words in a given tape.  The generator should import the library using the `/+` faslus rune and return the number of words in a text sample.  Submit the generator as your answer here.

- Q8. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 4?