# `%hw6`

Homework #6 for Hoon School Live.  
  
Let's use doors to build some new tools.  
  
You have learned about the following runes:  
  
- `?>` wutgar, branch on a positive assertion  
- `?<` wutgal, branch on a negative assertion  
- `?~` wutsig, branch on a null result  
- `+$` lusbuc, produce a type builder arm

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your ship, not your fakeship.)

- Q1. Produce a Hoon expression which makes a map which has Shakespeare characters as keys and the corresponding play as the value.  (This does not need to be a jar; you can just include one play for characters that recur in multiple plays.)  You may use ++my or ++put:by or another means to construct the map.  Make sure it has at least four elements.
```
> `(map @t @t)`(my ~[['Juliet' 'Romeo and Juliet'] ['Hamlet' 'Hamlet'] ['Othello' 'Othello'] ['Macbeth' 'Macbeth']])
{ [p='Juliet' q='Romeo and Juliet']
  [p='Hamlet' q='Hamlet']
  [p='Macbeth' q='Macbeth']
  [p='Othello' q='Othello']
}
```

##  Caesar cipher

The Caesar cipher code is an excellent example of an Urbit generator built with many arms.  You should closely read it, and I recommend even printing or drawing it and putting arrows to track its behavior.

- Q2. Extend the generator to allow for use of characters other than a-z.  It should also permit characters .,;:'" and you may have it rotate those the same way as letters are rotated.
```
:: included the new character at the end of tha arm alpha
++  alpha  "abcdefghijklmnopqrstuvwxyz.,;:"
```

- Q3. Build a gate that can take a Caesar-shifted tape and produce all possible unshifted tapes as a list of tapes.  This should be performed using the original a-z only cipher.
```
|=  msg=tape
=<
^-  (list tape)
=|  ret=(list tape)
=/  maxshift  (sub 'z' 'a')
=/  steps  1
|-
?:  (gth steps maxshift)
ret
$(ret (snoc `(list tape)`ret +:(caesar msg steps)), steps +(steps))
```

- Q4. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 6?