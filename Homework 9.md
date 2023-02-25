 `%hw9`

Homework #9 for Hoon School Live.  
  
It's time to verify our code's behavior and share it with the world!

- Q0. What is your planet or comet?  (Type "our" in the Dojo of your ship to identify if you're not sure—your ship, not your fakeship.)

- Q1. In %hw5 you produced a gate which calculated Euler primes.  Write a test suite for your arm.  It should test at least four different cases, one of which should be a failure to calculate (e.g. is there input it should crash on?).
```
/+  *test, *h5

|%
++  test-prime-5
  =/  u
  (find `(list @ud)`~[5 7 11 17] (prime 5))
  %+  expect-eq
    !>  0
    !>  (need u)
::
++  test-prime-2
  =/  value  (prime 2)
  ;:  weld
  %+  expect-eq
    !>  1
    !>  (lent value)
  %+  expect-eq
    !>  2
    !>  (snag 0 value)
  ==
::
++  test-prime-1
  %+  expect-eq
    !>  `(list @ud)`~
    !>  (prime 1)
::
++  test-prime-input
  %-  expect-fail
    |.  (prime 0)
--
```

- Q2. In %hw5 you produced a door which carried out calculator arithmetic functions  Write a test suite for your door.  It should test at least three different cases for each arm.  You should check for failure to compute with subtraction underflow (i.e. 5-7).

```
/+  *test, *h5

|%
++  test-add
  =/  g  ~(add calc 10)
  ;:  weld
  %+  expect-eq
    !>  10
    !>  (g 0)
  %+  expect-eq
    !>  11
    !>  (g 1)
  %+  expect-eq
    !>  1.010
    !>  (g 1.000)
  ==
::
++  test-sub
  =/  g  ~(sub calc 10)
  ;:  weld
  %+  expect-eq
    !>  10
    !>  (g 0)
  %+  expect-eq
    !>  9
    !>  (g 1)
  %-  expect-fail
    |.  (g 15)
  ==
::
++  test-mul
  =/  g  ~(mul calc 10)
  ;:  weld
  %+  expect-eq
    !>  0
    !>  (g 0)
  %+  expect-eq
    !>  10
    !>  (g 1)
  %+  expect-eq
    !>  100
    !>  (g 10)
  ==
::
++  test-div
  =/  g  ~(div calc 10)
  ;:  weld
  %+  expect-eq
    !>  10
    !>  (g 1)
  %+  expect-eq
    !>  1
    !>  (g 10)
  %-  expect-fail
    |.  (g 0)
  ==
--
```

- Q3. Collect a generator or library from a previous homework assignment.  Host it on a new desk on a moon of your primary ship.  Use the generator or library name plus a random unpredictable name for the desk (so we don't have to worry about collisions, e.g. calc-12345) and mark it |public.  Let us know which moon you have it running on and we'll sync it and install it.  (You could host on your main ship; the real issue is leaving the source ship running at least until we can check it.)

- Q4. What are your biggest remaining concerns, points of misunderstanding or fuzzy understanding, or other feedback on Lesson 9?