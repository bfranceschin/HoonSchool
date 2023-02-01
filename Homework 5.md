# `%hw5`

Homework #5 for Hoon School Live.  
  
One of the most common kinds of cores in Hoon is the door.  A door is sort of a gate-builder, which uses its arms to produce gates on demand (e.g. for particular types/auras/molds).  
  
You have learned about the following runes:  
  
- `|_` barcab, for producing a door  
- `%~` censig, to "pull an arm" in a door, or use a door to build a new gate and evaluate it  
- `|^` barket, for producing a core with a `$` default arm  
- `|.` bardot, for producing a trap to be evaluated at a later time  
- `|:` barccol, for producing a gate with a custom sample  
- `!:` zapcol, to turn on debugging in a library or generator file  
- `$_` buccab, to define a default sample (other than the bunt) in a core

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your ship, not your fakeship.)

- Q1. Write a gate named ++decrement that implements decrement without using the standard library functions of ++sub or ++dec.  (Hint:  Count up to one less than the input value using recursion).
```
|%

++  decrement
    |=  n=@ud
    ^-  @ud
    ?:  =(0 n)  !!
    =/  count  0
    |-
    ?:  =(+(count) n)
    count
    $(count +(count))

--
```

- Q2. A prime number is a number which is only divisible by itself and one (it has no factors), such as 2, 3, 5, 7, and 11.  Write a gate named ++primes which produces the Euler primes as a list.  The Euler primes are given by k²-k+n (for k = 1 to n-1).  (Note:  Your program will produce a set of primes if given one of "Euler's lucky numbers": 1, 2, 3, 5, 11, 17, or 41.)  See [https://number.subwiki.org/wiki/Lucky_number_of_Euler](https://number.subwiki.org/wiki/Lucky_number_of_Euler) for a table of example values.
```
++  prime
    |=  n=@ud
    ^-  (list @ud)
    =/  return  *(list @ud)
    =/  k  1
    |-
    ?:  (gte k n)
    return
    =/  e  (add (sub (mul k k) k) n)
    $(return (weld return ~[e]), k +(k))
```

- Q3. Consider the gate `|=(a=@ud (add 1 a))`.  What is the compiled battery of this gate?
```
> -:|=(a=@ud (add 1 a))
[8 [9 36 0 8.191] 9 2 10 [6 [7 [0 3] 1 1] 0 14] 0 2]
```

- Q4. Write an arm named ++factorial which calculates the factorial of a value.  Make its default sample value for the input be 1 using either `$_` or `|:`.  Make sure that 0! results in the value 1.  Answer with the |% core containing the arm.  
```
|%

++  factorial
|=  n=_1
=/  f  1
=/  counter  1
|-
?:  (lte counter n)
%=  $
    f  (mul f counter)
    counter  (add counter 1)
==
f

--
```

- Q5. Write a door (named calc if used in Dojo) that takes a @ud sample.   It should have four arms to handle multiplication, subtraction, addition, and division against this value.  For instance, you should be able to build an addition gate with `~(add calc 3)` and use it with `(~(add calc 3) 5)` to result in 8.  Answer with the door (no containing core necessary, thus no outer arm name); this could be a /lib library file for instance.  
```
|%

++  calc
    |_  n=@ud
    ++  add
        |=  x=@ud
        (^add n x)
    ++  sub
        |=  x=@ud
        (^sub n x)
    ++  mul
        |=  x=@ud
        (^mul n x)
    ++  div
        |=  x=@ud
        (^div n x)
    --

--
```

- Q6. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 5?