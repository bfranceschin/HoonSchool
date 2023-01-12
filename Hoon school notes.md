#urbit #hoon #dev #edu

### Lesson 1
##### youtube description
- A noun is an atom or a cell. An atom is an unsigned integer. A cell is a pair of two nouns. 
- An aura is a metadata “interpretation” of an atom. 
- “Functional” expressions always result in a value. 
- You preserve a value with a name (“face”) in Hoon using a `=/` tisfas rune. 
- You make a decision between alternatives in Hoon using a `?:` wutcol rune. 
- You can use existing code (“gates” = “functions”) in Hoon using a `%-` cenhep.

##### Notes
- Double spaces (or more) is a gap. Gap separates the children of runes
- :- is colhep, it turns the arguments in a cell


### Lesson 2
##### youtube description
- Many runes have irregular syntax, called “sugar syntax”. This makes it easier to write aesthetically communicative Hoon code. 
- Molds define Hoon structures. They have a default value (“bunt”) and are strictly statically typed (i.e. they must match).  
- Find the type of a value using the zapgar rune.  
- Use comments (`::`) to explain the logic of any code you produce.  
- A gate (made with `|=` bartis) lets you store a computation for future use.  
- You can store a gate as a standalone reusable file called a generator.  
- You can build code from a file directly with `-build-file` or import its contents with `/+` from `/lib`.

##### Notes
- What the \`\` does?
	- It is kind of a cast?
- Forget the negative numbers for now
- ^-  enforce a type constraint
- For now, to define a named function, we have to create a file to it
- For running the demo:
	- Mount __base__: 
	 ```> |mount %base```
	  This "__reveals__" the base folder to the host operating system. (he calls the host operating system __earth__ and the urbit os __mars__)
	   - We created the __demo.hoon__ file on __zod/base/gen__.
	- To apply the changes to __mars__, it is necessary to "__sync__" both OSs by calling the command
	 ```> |commit %base```
- Generator file is like a script
- 3 kinds of types:
	  - __atoms__: values with auras
	  - __molds__: data structures (cells, list, etc)
	  - __marks__: file types
   - A __bunt__ is the default value of a type
   - __list__ is a nul terminated tuple
	   - Is possible to have a list of different types