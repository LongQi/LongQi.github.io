---
layout: post
---

#The Book of Ruby#

**The Ruby Library Documentation**

Refer to this online documentation which is shown in a multi-pane web page:

[http://www.ruby-doc.org/core](http://www.ruby-doc.org/core)

Alternatively, here you can browse the library alphabetically:

[http://www.ruby-doc.org/stdlib](http://www.ruby-doc.org/stdlib)

There is also a page from which the library documentation may be downloaded in various formats, versions and languages:

[http://www.ruby-doc.org/downloads](http://www.ruby-doc.org/downloads)


##Chapter 1 Strings, Numbers, Classes and Objects##

	print("Enter your name:")
	name = gets()
	puts("Hello, #{name}")

`s.to_f` is a method of the String class. It attempts to convert the string to a floating point number. If the string cannot be converted, 0.0 is returned. So fo instance, "Hello world".to_f would return 0.0.

**Classes and Objects**

A class is the blueprint for an object. It defines the data an object contains and the way it behaves. Many different objects can be created from a single class.

Instance Variables, beginning with the @, that means that they belong to individuals objects - or instances of the class. It is not necessary to pre-declare instance variables.

For the pure object orientation, the data inside each object is private.

**Inspecting Objects**

+1.inspect, returns a string containing a human-readable representation of the object. Ruby also provides the p method as a shortcut to inspecting objects and printing out their details, like this: p(anobject).

##Chapter 2 Class Hierarchies, Attributes and Class Variables##

Class Hierarchies - Ancestors and Descendants. Each class in Ruby has only one parent.

	def description
		return @description
	end

	def description=(aDescription)
		@description = aDescription
	end

Here, the get accessor is called description and the set accessor is called description=. It is now possible to assign a new string like this:

	t.description = "a bit faded and worn around the edges"

And you can retrieve the value like this:

	puts(t.description)

The SET Accessor, this is correct:

	def name=(aName)

But this is an error:

	def name = (aName)

**Attribute Readers and Writers**

attr_reader and attr_writer:

	attr_reader:description
	attr_writer:description

You should add this code inside your class definition like this:

	class Thing
		attr_reader:description
		attr_writer:description
	end

`attr_reader(:description)` creates an instance variable with the name, @description, and an accessor method named description(). `attr_accessor` method provides a shorter alternative to using both `attr_reader` and `attr_writer`.

**Calling Methods of A Superclass**

	super(aName, aDescription)

**Class Variables**

@@num_things, define this to be a class variable.


##Chapter 3 Strings and Ranges##

Double-quoted strings do more work than single-quoted strings.

###String Handling

**Concatenation**

You can concatenate strings using << or + or just by placing a space between them.

	s = "Hello"<<"world"
	s = "Hello"+"world"
	s = "Hello" "world"

s is assigned the string "Hello world".

	s = "Hello world"
	puts(s[1,3])	#prints out 'ell'
	puts(s[-1,1])	#prints out 'd'
	puts(s[-5,1])	#prints out 'w'
	puts(s[-5,5])	#prints out 'world'

	puts(s[-5..5])	#this prints an empty string!
	puts(s[-5..-1])	#prints 'world'

**Chop and Chomp**

The chop and chomp methods can be used to remove characters from the end of a string. The chop method returns a string with the last character removed or with the carriage return and newline characters removed if there are found at the end of the string. The chomp method returns a string with the terminating carriage return or newline character removed.

The Record Separator - $/

	$/="world"
	s = gets()	#user enters "Had we but world enough and time..."

	puts(s)	#displays "Had we but world"

In most cases, chomp is preferable as it won't remove the final character unless it is the record separator (a newline) whereas chop will remove the last character no matter what it is.

	s1 = "Hello world
	"
	s2 = "Hello world"
	s1.chop		#returns "Hello world"
	s1.chomp	#returns "Hello world"
	s2.chop		#returns "Hello worl"
	s2.chomp	#returns "Hello world"

The chomp method lets you specify a character or string to use as the separator:
	
	s2.chomp('rld')		#returns "Hello wo"

##Chapter 4 Arrays and Hashes##

In Ruby, a single Array can contain items of mixed data types such as strings, integers and floats or even a method-call which returns some value:

	a1 = [1,'two',3.0,array_lenght(a0)]
	a = Array.new(2,"hello world")		#["hello world","hello world"]
	a = Array.new		#an empty array

	a = Array.new(2)
	a[0] = Array.new(2,'hello')
	a[1] = Array.new(2,'world')

**Iterating over Arrays**

	multiarr = [['one','two','three','four'],[1,2,3,4]]
	
	for i in multiarr
		puts(i.inspect)
	end

	=begin
	This displays:
		["one","two","three","four"]
		[1,2,3,4]
	=end


	for row in multiarr
		for item in row
			puts(item)
		end
	end

**Copying Arrays**

	arr1 = [1,2,3,4,5]
	arr2 = arr1		#arr2 is now the same as arr1. Change arr1 and arr2 changes too!
	arr3 = arr1.clone	#arr3 is a copy of arr1. Chanage arr1 and arr2 is unaffected.

**Compare Arrays**

comparison operator <=>. `arr1<=>arr2`.It returns -1 if arr1 is less than arr2; it returns 0 if arr1 and arr2 are equal; it returns 1 if arr1 is greater than arr2. It turns out that it compares each item in one array with the corresponding item in the other.

	[0,10,20]<=>[0,20,20]

However, if two such arrays are compared and one of the elements in the shorter array is greater than the corresponding element in the longer array, then the shorter array is deemed to be greater.

**Comparing Values**

You can override the < = > method to enable you to define exactly how comparisons will be made between specific types of object.

	class MyArray < Array
		include Comparable

		def <=> (anotherArray)
			self.length <=> anotherArray.length
		end
	end

	myarr1 = MyArray.new([0,1,2,3])
	myarr2 = MyArray.new([1,2,3,4])

	myarr1 <=> myarr2		#returns 0

###Hashes###

**Creating Hashes**

	h1 = Hash.new
	h2 = Hash.new("Some kind of ring")

	h2['treasure1'] = 'Silver ring'
	h2['treasure2'] = 'Gold ring'
	h3['treasure3'] = 'Ruby ring'
	h4['treasure4'] = 'Sapphire ring'

In principle, the key can be any type of object. 

	h1 = {	'room1'=>'The Treasure Room',
			'room2'=>'The Throne Room',
			'loc1'=>'A Forest Glade',
			'loc2'=>'A Mountain Stream'
			}

**Copying a Hash**

	h5 = h1.clone

**Hash Methods**

	aHash.delete(someKey)
	aHash.has_key?(someKey)
	aHash.has_value?(someValue)
	aHash.invert		#return a new hash created using the original hash's values as keys, and its keys as values.
	aHash.keys			#return an array populated with the hash's keys.
	aHash.values		#return an array populated with the hash's values.

##Chapter 5 Loops and Iterators##

###For Loops###

	for i in [1,2,3] do
		puts(i)
	end

	[1,2,3].each do |i|
		puts(i)
	end

###Blocks###

	[[1,2,3],[3,4,5],[6,7,8]].each do
		|a,b,c|
			puts("#{a},#{b},#{c}")
	end

	[[1,2,3],[3,4,5],[6,7,8]].each{
		|a,b,c|
			puts("#{a},#{b},#{c}")
	}

###While Loops###

	while tired
		sleep
	end

	begin
		sleep
		snore
	end while tired

###Until Loops###

`until` = `while not`

	until i==10
		puts(i)
		i+=1
	end

###Loop###

	loop{
		puts(arr[i])
		i+=1
		if(i==arr.length) then
			break
		end
	}

##Chapter 6 Conditional Statements##

###Case Statements###

##Chapter 7 Methods##

###Class Methods###

	class MyClass
		def MyClass.classMethod
			puts("This is a class method")
		end
	
		def instanceMethod
			puts("This is an instance method")
		end
	end

You should use the class name when calling a class method:

	MyClass.classMethod

A specific object cannot call a class method. Nor can a class call an instance method:

	MyClass.instanceMethod	#Error!
	ob.classMethod			#Error!

###Class Variables###

	class Thing
		@@num_things = 0
	
		def initialize(aName,aDescription)
			@@num_things += 1
		end
	end

Unlike an instance variable, a class variable must be given a value when it is first declared:

	@@classvar = 1000

