# Dwarf

Dwarf is a very small scripting language that will ease concurrency.
Dwarf is heavily influenced by language like Lisp and OCaml.

# Dwarf-Interpreter

The interpreter for dwarf is written in Elixir. 

To interpret a source program run 

```
mix escript.build 		# in the main folder
# this will generate an executable dwarf file
./dwarf path-to-file.dw     # this will start the interpretition of the script
```
## Language description
-----------------------

The language will have very simple operations and expressions.
```
expr :=  
		| binary operation            --- such as `+` `-` etc
	   | unary operation             --- "!"
	   | `true`, `false`             --- booleans
	   | number                      --- integer such as `7`,`8`,`9` no floats yet
	   | function call = foo(args)   --- `get()`, `square(3)"`
	   | (expr)                      --- bracketed expression `(2 + 3) * 2`

args := 
		| list of expr (expr,expr)     --- arguments passed to a function call
	   | expr

params := 
		 | (identifier : type)          --- a parameter of a function declaration
		 | (identifier : type ) params  --- parameters of a function declaration

stmt :=  
		| `if` expr `then` stmt `else` stmt    --- if then else statement
	   | assign with equal 					  --- assignment such as `a = 3 + 2` where a has already been declared
	   | var_dec with :=                      --- declaration and assignment of a new variable `int a := 3 + 2`
	   | { stmts }							  --- a list of statements
	   | print ident 						  --- print a value to the command line
	   | function                             --- declaration of  a function

stmts := 
		| stmt stmts                 --- statements are a list of statement
		| epsilon                    --- stop the looping


function := 
			| fun type identifier params { stmts }     --- declaration of a function, returns the last computed value 

type :=  
		| int 					   --- variable can be of three types at the moment int, boolean, fun
	   | boolean 
	   | fun
```
