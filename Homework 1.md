#urbit #hoon #dev #edu #homework



#   `%hw1`

Homework #1 for Hoon School Live.  
  
Homework exercises have two purposes for us:  to help validate that you have learned the material that corresponds to a particular lesson, and to stretch you in grasping and applying the relevant concepts.  
  
In particular, you learned about the following runes:  
  
- `%-` cenhep, for applying a function  
- `^-` kethep, for enforcing or converting the type of a value  
- `:-` colhep, for making a cell (pair of nouns)  
- `=/` tisfas, for assigning a name to a value  
- `?:` wutcol, for making a decision

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your actual ship, not your fakeship.)

## Atoms

Atoms are bare values, but they have a type or aura which lets you distinguish, say, a 1 in binary 0b1 from a 1 in hexadecimal 0x1.

- Q1. Find your planet's number by converting your ship’s name to a `@ud` aura.
 ```
 > %-  @ud  ~tiptec-mogmev
74.118.437
> `@ud`~tiptec-mogmev
74.118.437
 ```
 

- Q2. Find your planet's hexadecimal number by converting your ship’s name to a `@ux` aura.
```
> `@ux`~tiptec-mogmev
0x46a.f525
```

- Q3. What are the types (auras) of each of the following atoms?  Consult https://developers.urbit.org/reference/hoon/auras if you can't tell offhand.  

`@ud` unsigned decimal
`@ub` unsigned binary
`@ux` unsigned hexadecimal
`@t` utf-8
`@da` absolute date
`@rs` floating point single precision
`@p` phonemic base (ship name)

`1.000`
`0b11.1001`
`0x7fa.45e2`
`'hello Mars'`
`~1992.1.12..15.05.00`
`.2.718281828`
`~sampel-palnet`

##  Cells

Read about the `:` col family of runes in the docs:  
  
[https://urbit.org/docs/hoon/reference/rune/col](https://urbit.org/docs/hoon/reference/rune/col)  
  
These build cells of various sizes (e.g. [1 [2 3]], etc.).

- Q4. Create a duple, or 2-tuple, of 1 and 2, using a single col rune.
```
> :-  1  2
[1 2]
```

- Q5. Create a triple, or 3-tuple, of 'a', 'b', and 'c', using a single col rune.
```
> :+  'a'  'b'  'c'
['a' 'b' 'c']
```

- Q6. Create a quadruple, or 4-tuple, of ~zod, ~nec, ~bud, and ~wes, using a single col rune.
```
> :^(~zod ~nec ~bud ~wes)
[~zod ~nec ~bud ~wes]
```

##  Pinning Values

The =/ tisfas rune is helpful for preserving (“pinning”) values with names for use in subsequent expressions.  For each of these, you should respond with the Hoon expression, not the resulting value.

- Q7. In one expression, pin a value `three` and calculate 3×3 using the ++mul function (gate).
```
> =/  three  3 
  %-  mul  [three three]
```

- Q8. In one expression, pin two values `ten` and `hundred` and calculate 10¹⁰⁰ using the ++pow function (gate).
```
> =/  ten  10 
  =/  hundred  100
  %-  pow  [ten hundred]
```

##  Making Decisions

We can cause a computation to choose between two alternatives using the `?:` wutcol rune.

- Q9. Implement the piecewise boxcar function in Hoon.  Since we can't store expressions for future use yet, use 4 for the example input value (but pin it to a face `x`).  (:= is not a rune, it's the mathematical symbols for "defined as".  You can read it as an equals sign.)  
  
That is, your answer will look something like this, i.e. multiple lines (for x²):  
  
```
=/  x  2  
(mul x x)
```

![](https://lh4.googleusercontent.com/WlI6c18pNF3MT06ZXkmHiVur2yU8GFDlaWwmFB2rS6CpOHG_hO7BDnajgICvgnZwZBo5GbNTpMmEQDeKuXcm2WubU8tvo1PU0_TBKCxYYwbnoBCCUkDIq7D0zKSLq44JnIkT7J3WYMIF1StVHZY-WTHSLobaUqWrd3JanplXPkwrtwRDdAkt6e-BhG24Fxazr1HO)

```
> =/  x  4
  ?:
  ?&  (gth x 3)
  (lte x 5)
  ==
  1
  0
```

- Q10. Implement the piecewise triangle function in Hoon.  Since we can't store expressions for future use yet, use 2 for the example input value (but pin it to a face `x`).  (:= is not a rune, it's the mathematical symbols for "defined as".  You can read it as an equals sign.)  
  
That is, your answer will look something like this, i.e. multiple lines (for x²):  
  
```
=/  x  2  
(mul x x)
```

![](https://lh3.googleusercontent.com/mTMXcMr2wi4pUSC3ThN7nOVxl_Ou5Oq4UNMiFhjr9cqyt-6mtZFjYwjqYzv8gTtrK7JNe5UfytmO9guGiWBZsxHyqL-x3grQeVzLCdY0at7sHY3u-tLjWpSlADmZylrlxeZAdRtLlwNvzshpd5LRvsLPhmRmB5dJQPC2SspUSh62gQ38qs6mFCWZBI2cngyUoIuf)

```
=/  x  2
  ?:  ?&  (gth x 2)  (lte x 3)  ==
  (sub x 2)
  ?:  ?&  (gth x 3)  (lte x 4)  ==
  (sub 4 x)
  0
```

##  Hoon Pronunciation

What are the pronounced names of each of the following runes?

- Q11. `%=` centis

- Q12. `$:` buccol

- Q13. `:*` coltar

- Q14. `~&` sigpam

- Q15. `|-` barhep

- Q16. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 1?

test