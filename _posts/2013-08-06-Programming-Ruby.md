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

###Reading and 'Riting###

`puts` writes each of its arguments, adding a newline after each.

`print` also writes its arguments, but with no newline.

`printf` prints its arguments under the control of a format string.

	printf "Number: %5.2f, String: %s", 1.23, "hello"

produces:
	
	Number: 1.23, String: hello

`gets` returns the next line from your program's standard input stream

	line = gets
	print line

The `gets` routine has a side effect: as well as returning the line just read, it also stores it into the global variable $\_. This variable is special, in that it is used as the default argument in many circumstances. If you call `print` with no argument, it expression is matched against $\_.

##Classes, Objects, and Variables##

	class Song
		def initialize(name, artist, duration)
			@name = name
			@artist = artist
			@duration = duration
		end
	end
	
	aSong = Song.new("Bicylops","Fleck",260)
	aSong.inspect
	#"#<Song:0x401b4924 @duration=260, @artist=\"Fleck\",@name=\"Bicylops\">"

