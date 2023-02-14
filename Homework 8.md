# `%hw8`

Homework #8 for Hoon School Live.  
  
_L'état, c'est moi.__  (Louis XIV)  

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your ship, not your fakeship.)

- Q1. Take your calculator door from previous homework and compose it into a %say generator that uses =< tisgal and =~ tissig to carry out a sequence of calculations.  (Thus the door should be in the same file, not included as a library.)  
```
:-  %say
|=  *
:-  %noun
=<  =~  calc
      (add 100)
      (add 100)
      (sub 50)
      (mul 2)
      (div 100)
      n
    ==
|%
++  calc
    |_  n=@ud
    ++  add
        |=  x=@ud
        +>.$(n (^add n x))
    ++  sub
        |=  x=@ud
        +>.$(n (^sub n x))
    ++  mul
        |=  x=@ud
        +>.$(n (^mul n x))
    ++  div
        |=  x=@ud
        +>.$(n (^div n x))
    --
--
```

- Q2. Convert your FizzBuzz program to produce a tank (formatted print tree).  Produce a %say generator that yields a ++ram-ed version of this output, bounded by "(" pal and ")" par, and separated by "|" bar.  
```
:-  %say
|=  *
:-  %noun
=<  
~(ram re [%rose ["|" "(" ")"] (fizzbuzz 30)])
|%
++  fizzbuzz
    |=  n=@ud
    =>
    |%
    ++  func
        |=  n=@
        ^-  @ta
        ?:  =((mod n 15) 0)
        'fizz buzz'
        ?:  =((mod n 5) 0)
        'buzz'
        ?:  =((mod n 3) 0)
        'fizz'
        (scot %ud n)
    --
    =/  l  (gulf 1 n)
    (turn l func)

--
```

- Q3. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 8?