---
layout: post
---
#Programming Ruby#

##Running Ruby##

There are two ways to run Ruby-interactively and as a program.

Ruby is an genuine object-oriented language.

##Ruby.new##

###Some Basic Ruby###

Methods are difined with the keyword `def`, followed by the method name and the method's parameters between parentheses. You simply finish the body with the keyword `end`.

	def sayGoodnight(name)
		result = "Goodnight, "+name
		result = "Goodnight, #{name}"
		return result
	end

Local variables, method parameters, and method names should all start with a lowercase letter or with an underscore. Global variables are prefixed with a dollar sign ($), while instance variables begin with an (@). Class variables start with (@@). Finally, class names, module names, and constants should start with an uppercase letter.

###Arrays and Hashes###

	a = [1, 'cat', 3.14]
	
	#create empty arrays
	empty1 = []
	empty2 = Array.new

Ruby hashes's literal must supply two objects for every entry: one for the key, the other for the value.

	instSection = {
		'cello' => 'string'
		'clarinet' => 'woodwind'
		'drum' => 'brass'
	}

	#create empty hash
	emptyHash = Hash.new(0)

###Control Structures###

	if count > 10
 		puts "Try again"
	elsif tries == 3
		puts "You lose"
	else
		puts "Enter a number"
	end

while statements:

	while weight < 10
		numPallets += 1
	end

can be written to:(when the if or while statement is just a single expression)

	numPallets += 1 while weight < 10

