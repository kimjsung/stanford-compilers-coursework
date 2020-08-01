# Stanford Compilers Coursework
### Table of Contents

1. [Introduction](#introduction)

## Introduction
This is a repository of coursework assignments for the [Stanford Compilers](https://online.stanford.edu/courses/soe-ycscs1-compilers) MOOC course.
The result of completing all coursework assignments is a fully-working compiler for the [COOL Programming Language](http://theory.stanford.edu/~aiken/software/cool/cool.html).

The compiler compiles COOL into MIPS Assembly. MIPS is a reduced instruction set architecture about which you can learn more [here](https://en.wikipedia.org/wiki/MIPS_architecture).
Resulting programs are run using [SPIM simulator](http://spimsimulator.sourceforge.net/).

COOL (Classroom Object Oriented Language) is a computer programming language designed by Alexander Aiken for use in a compiler course taught at Stanford.
COOL resembles many modern programming languages, including features such as objects, automatic memory management, strict static typing and simple reflection.
COOL constructs take a few ideas taken from functional programming languages, so that every COOL statement is an expression which must return something.

COOL is precisely defined in specification documents, the most relevant ones are:
  * [COOL Manual](http://theory.stanford.edu/~aiken/software/cool/cool-manual.pdf)
    * describes lexical and syntactical structure of the language
    * describes type system rules (equations) and language operational semantics
  * [COOL Runtime System](https://theory.stanford.edu/~aiken/software/cooldist/handouts/cool-runtime.pdf)
    * describes the runtime system backing this programming language
    * describes garbage collection algorithms used and the interface between those and a correct compiler
    * describes the object layout recommended to implement this language and the interface to the garbage collection routines
    
 Here are a few examples of simple COOL programs:
 
 [Hello world](./examples/hello_world.cl)
 ``` cool
 class Main inherits IO {
   main(): SELF_TYPE {
	out_string("Hello, World.\n")
   };
};
 ```
 
 [Palindrome checking program](./examples/palindrome.cl)
 ``` cool
 class Main inherits IO {
    pal(s : String) : Bool {
	    if s.length() = 0 
          then true
	    else if s.length() = 1 
          then true
	    else if s.substr(0, 1) = s.substr(s.length() - 1, 1) 
          then pal(s.substr(1, s.length() -2))
	    else false
	    fi fi fi
    };

    i : Int;

    main() : Object {
      {
          i <- ~1;
          out_string("enter a string\n");
          if pal(in_string())
              then out_string("that was a palindrome\n")
              else out_string("that was not a palindrome\n")
          fi;
      }
    };
};

 ```
