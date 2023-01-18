   `%hw3`

Homework #3 for Hoon School Live.

With the introduction of cores, you are now equipped to build Hoon generators that can also function as libraries.

You have learned about the following runes:

- `|-` barhep, for producing a trap (like a loop or repetition label)
- `.+` dotlus, for increasing a value by one
- `.=`, for checking equality/equivalence of two values
- `%=` centis, for "rebooting" the current code with new values
- `|%` barcen, for collecting many functions and values in one core
- `++` luslus (actually a digraph, not a rune, but that's technical), for labeling a gate
- `+$` lusbuc (ditto), for labeling a type
- `=<` tisgar, for
- `=>` tisgal, for
- `~&` sigpam, for output as a debugging or messaging tool

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your ship, not your fakeship.)

- Q1. You work in a lab.  The lab uses a scale which is inaccurate for values less than 10 grams.  Any weight less than that should simply register as zero in your measurements.  Write a gate in an arm `++corrected-weight` which checks whether the value is less than 10 and returns zero if it is, otherwise returns the normal value.  (Answer with the arm as the only arm in a regular |% core.)
```
|%
++  corrected-weight
    |=  w=@ud
    ^-  @ud
    ?:  (lth w 10)
    0
    w
--
```

- Q2. The lab needs to know the total quantity of reagent (in grams) you've been able to produce in the past week.  You have the totals for every day.  Write a gate in an arm `++weekly-reagent` which uses a trap to add up the seven values it receives in a 7-element list.  E.g., `~[134 287 12 0 127 194 0]` should sum to 754.  (Answer with the arm as the only arm in a regular |% core.)
```
|%
++  weekly-reagent
    |=  l=(list @ud)
    =/  counter  0
    =/  sum  0
    |-
    ?:  =(counter 7)
    sum
    %=  $
        sum  (add sum -:l)
        l  +:l
        counter  +(counter)
    ==
--
```

- Q3. Produce a type arm named `reptile` using +$ lusbuc which is a type union ($? bucwut) for several reptiles of your choice.  (E.g. if I were doing this for amphibians, I could use %frog, %toad, and %salamander.)  Provide at least four options in the type union.  (The `%word` syntax is a "term", or internal constant value we can use to label things in Hoon:  previewing this a bit!)

- Q4.  Produce a gate (generator) which accepts a list of values and prints out each value in order on a separate line.

  For example, given the `(list @)` `[1 2 3 4 5 ~]`, the generator should  print out
  
  ```
  '1'
  '2'
  '3'
  '4'
  '5'
  ```

  You do not need to store these values in a list; simply output them at each step using `~&` sigpam and return the final value.  Sigpam does *not* return a value, it simply displays a result and then continues to the next line (its second child).

  You can retrieve the n-th element in a list using the `++snag` gate:
  
  ```
  > =/  n  0  (snag n [1 2 3 4 5 ~])
    1
  ```
  
  (Note that `++snag` counts starting at zero, not one.)
  
  You can get the length of a list using `++lent`.
  
  You can check for whether two values are equal using `=(1 2)` syntax (irregular form of `.=` dottis).
```
++  print-list
    |=  l=(list @)
    |-
    ?~  l
    l
    ~&  i:l
    $(l t:l)

++  print-list-counter
    |=  l=(list @)
    =/  counter  0
    =/  len  (lent l)
    |-  
    ~&  (snag counter l)
    ?:  (lth counter (dec len))
    %=  $
        counter  +(counter)
    ==
    counter
```

- Q5.  Produce a gate (generator) which accepts a list of values and prints out each value in *reverse* order on a separate line.

  For example, given the `(list @ux)` `[0x0 0x1 0x2 ~]`, the generator should  print out

  ```
  0x2
  0x1
  0x0
  ```
  
  Your code from the previous exercise should work with modest changes.
```
:: incorrect, it is printing the ~, could not fix it yet
++  print-list-reverse
    |=  l=(list @)
    ~&
        |-
            ?~  l
            l
            ~&  $(l t:l)
            i:l
    l

++  print-list-counter-reverse
    |=  l=(list)
    =/  len  (lent l)
    =/  counter  len
    ~&
        |-
        ?:  =(counter 1)
        (snag (dec counter) l)
        ~&  $(counter (dec counter))
        (snag (dec counter) l)
    counter
```

- Q6. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 3?
- The list manipulation it is still a little fuzzy for me and combining branching with ~&