#   `%hw2`

Homework #2 for Hoon School Live.  
  
You have now learned how to use irregular syntax for Hoon runes, and should think about how to employ it when convenient.  
  
You have learned about the following runes:  
  
- `^+` ketlus, for enforcing a type (like `^-` but with an example)  
- `^*` kettar, for producing an example (a bunt)  
- `!>` zapgar, for ascertaining the type of a value  
- `|=` bartis, for creating a gate  
- `::`, for commenting on code  
  
Not covered in the live lesson but in the notes:  
  
- `$?` bucwut, for producing a type union  
- `$:` buccol, for producing a named tuple  
- `!!` zapzap, for crashing or stubbing out incomplete branches of your Hoon expressions  
- `/+` faslus, for importing a library of code

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your ship, not your fakeship.)
```
~tiptec-mogmev
```

##  Irregular Syntax

Many runes have irregular syntax.  This can make it easier to write aesthetically expressive Hoon code.

- Q1. Convert the irregular form `[1 2 3 4]` to a regular form.
```
> :-  1
  :-  2
  :-  3
  4
```

- Q2. Convert the irregular form `(mul 10 5)` to a regular form.
```
> %-  mul
  :-  10
  5
```

- Q3. Convert the regular form `^-  @ud  ^-  @  'Mars'` to an irregular form.
```
> `@ud`'Mars'
```

##  Molds

Molds define Hoon structures.  They have a default value (“bunt”) and are strictly statically typed (i.e. they must match).

- Q4. What is the bunt of `@da`?

- Q5. What is the bunt of `@uc`?

- Q6. What is the bunt of `@da` as a `@ud`?  (I.e., bunt it then convert that value to @ud.)  

- Q7. What is the bunt of `cell`?  (I.e. there is a type in Hoon named `cell`, do it of that.)

- Q8. Produce a type union which can accept a signed or unsigned decimal integer.  (ETA:  actually not a good question since type unions can't distinguish auras, do it for practice but I'll have to take this one out next time around)  

- Q9. Produce a named tuple with three elements `x`, `y`, and `z`, all of type `@rs` (real number, number with a fractional part).

- Q10. What does the infixed `^` ket do?  E.g., `4^5`.  (Infer from its behavior in the Dojo.)

##  Deferring Computation

A gate (made with `|=` bartis) lets you store a computation for future use.  
  
You can store a gate as a standalone reusable file called a generator.

- Q11. Take your code for the boxcar function in the previous homework.  Produce a gate which works for any `@ud` input value `x`.  (Your answer should just be that gate, `|=` onwards.)  

![](https://lh3.googleusercontent.com/GircNC0W49Axuddqbw280FX7CYA53q70TXT1v_qp6OEFutcIcz5Kc1OnwRFbjLIgG9kMfRYuvawL5XWK7a6mb10Itiye6y22UOAX0pPDZOblTLR7IfiwDa6Iwx8PEDkKFVG4jw3fzxbhX89NVT32QTaJMKfkP6SSAmIxM7xgVTOHFBLhQTvtlWHVGfmZPsKJgos_)

- Q12. Take your code for the boxcar function gate in the previous question.  Produce a generator from the gate named `boxcar.hoon`.  Don't forget to add at least one comment to explain its intent.  (Your answer will be very similar to the answer for Q11.)

![](https://lh3.googleusercontent.com/GircNC0W49Axuddqbw280FX7CYA53q70TXT1v_qp6OEFutcIcz5Kc1OnwRFbjLIgG9kMfRYuvawL5XWK7a6mb10Itiye6y22UOAX0pPDZOblTLR7IfiwDa6Iwx8PEDkKFVG4jw3fzxbhX89NVT32QTaJMKfkP6SSAmIxM7xgVTOHFBLhQTvtlWHVGfmZPsKJgos_)

- Q13. Write a generator which accepts the value of a planet as a `@p` and returns the next neighbor, also as a `@p`.  The next neighbor of a planet is calculated by incrementing the numeric value of the planet's address by one.  You will then need to convert it from `@ud` back to `@p`.  (You don't need to filter for planet input or anything, just for `@p`.)  For instance, the next neighbor of ~sampel-palnet is ~radbyr-fonlyr.

- Q14. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 2?