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

###Getting Input###

`gets` is the Ruby method that gets input from the user.

	variable_name = gets.chomp


###Printing the Output###

	first_name = "Kevin"
	puts "Your name is #{first_name}!"


###Formatting with String Methods###

`.capitalize`, it capitalizes the first letter of a string and makes the rest of the letters lower case.

When you call something like `.capitalize` on a string, you're not capitalizing that exact string. Ruby makes a copy of the string, capitalizes that, and that's what it returns. If you want to capitalize the string you've already got, though, you can make one small change: add a `!` to the end of the method name: `.capitalize!`

	"hello".capitalize!

will result in

	Hello


##Control Flow in Ruby##

	if, elsif, else, end

unless = if not

	hungry = false

	unless hungry
		print "I'm writing Ruby programs!"
	else
		print "Time to eat!"
	end

