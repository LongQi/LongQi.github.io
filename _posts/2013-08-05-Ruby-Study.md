---
layout: post
---
#Ruby Study#

- High-level, meaning reading and writing Ruby is really easy-it looks a lot like regular English.
- Interpreted, meaning you don't need a compiler to write and run Ruby.
- Object-oriented, meaning it allows users to manipulate data structures called objects in order to build and execute programs. Everything in Ruby is an object.
- Easy to use.

###Data Types###

three data types:

- numbers
- booleans
- strings

###'puts' and 'print'###

puts, it adds a new line after the thing you want it to print.

	puts "What's up?"

print, prints whatever you give it to the screen.

	print "Oxnard Montalvo"

###The '.length' Method###

	"I love Ruby".length

###The '.reverse' Method###
	
It spits out a backwards version of the string you gave it.

	"Eric".reverse
will result in

	"cirE"

###The '.upcase' and '.downcase' Method###

	puts "eric".upcase

will result in

	ERIC

###Comments###

Single-Line Comments, use '#':

	# I'm a full line comment!
	"Eric".length

Multi-Line Comments, start with `=begin` and end with `=end`, everything between those two expressions will be a comment.

	=begin
	I'm a comment!
	I don't need any # symbols.
	=end

