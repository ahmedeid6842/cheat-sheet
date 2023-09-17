<a name="readme-top"></a>

<h1 align="center"> Learn to Code with Ruby </h1>

<img src="https://sumatosoft.com/wp-content/uploads/2023/03/ruby-lang-ar21.png" />

- [Numbers](#section-1--numbers)
- [Strings](#section-2--strings)
- [Methods](#section-3--methods)
- [Conditions](#section-4--conditions)
- [Ranges](#section-5--ranges)
- [Arrays](#section-6--arrays)
- [ Arrays with iteration](#section-7--arrays-with-iteration)
- [Strings ||](#section-8-strings)
- [Array ||](#section-9-array-bonus)
- [Hashes](#section-10-hashes)
- [Ruby Blocks, Procs, and Lambdas](#section-11-ruby-blocks-procs-and-lambdas)
- [Classes](#section-12-classes)
- [Module](#section-13-module)
- [Classes ||](#section-14-classes)


# section 1 : Numbers

### Numbers methods

```ruby
# times
10.times do |counter| # repeat block n times
  puts counter
end

# upto 
10.upto(15) do |counter| # start from x and increment untill reach y 
  puts counter
end

# downto 
10.downto(5) do |count| # start from x and decrement untill reach y 
  puts count
end

# step
0.step(30, 2) { |counter| puts counter } # start from 0 to 30 and at each step add 2

# even - odd ? 
number = 10
puts 10.odd? # check if number is odd or event ... true/fase
puts 10.even? # check if even or not ... true/false

# single line block : if the block of code is one line you can use `{}`
10.times { |counter| puts counter }
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 2 : Strings

### Multi Line String

<aside>
📌 Instead of writing string between double quote, you can use `<<Lable` to highlight the MLS(Multi Line String)

</aside>

```ruby
multi_string= <<MLS

 this is my first string
here it my second line
MlS
```

### Concat

<aside>
📌 concat multiple string using `concat` method or `<<` or `prepend`
**Note:** concat method  overwrite the new string … `str.concat(str2)` = `str = str+str2`

</aside>

```ruby
str1 = "ahmed"
str2 = "eid"

puts str1.concat(str2) # "ahmedeid" ... after this step str1=ahmedeid
puts str1 << str2 # "ahmedeidahmed" ... << is same as concat
puts str1.prepend("Mahmoud") # "Mahmoudahmedeidahmed" prepend concat two string but add to the front 
```

### Length

<aside>
📌 To get length of string you can use `length` or `size` … both of them are the same

</aside>

```ruby
str1= "ahmed eid"
puts str1.length
puts str1.size
```

### Extract character

<aside>
📌 to extract a pattern or set of character from string we can use:  *`slice(,)` - `[,]` - `slice(..)` , `[..]`*

</aside>

```ruby
str1= "ahmed eid abdulrahim"

puts str1.slice(4, 4) # "d ei"
puts str1[4, 4] # "d ei"

puts str1.slice(4..11) # "d eid a"
puts str1[4..11]  # "d eid a"

puts str1.slice(4...8)  # "d eid ab"
puts str1[4...8] # "d eid ab"
```

- `slice(start_index,range)` or `[start_index, range]` : this slice start from index and take a slice until index + range
- `slice(start_index..end_index)` or `[start_index..end_index]` : this slice start from index to the end index -1 … exclude the end index character
- `slice(start_index…end_index)` or `[start_index…end_index]` : the different between the two and three dots slice is three dots include the end index but the two dots not

### string case

<aside>
📌 S*tring case - `upcase` - `downcase` - `swapcase` - `capitalize`*

</aside>

```ruby
str1= "ahmed eiD"

puts str1.capitalize # "Ahmed eiD" ... captialize the first charcter of string
puts str1.upcase # "AHMED EID" .. make all character upper case
puts str1.downcase # "ahmed eid" .. make all character small case
puts str1.swapcase # "AHMED EId" .. convert the captial charcater to small chacter and vice verse
```

### `reverse` , `bang` , `include?` , `empty?` , `nil?`

```ruby
str1 = "ahmed eid"
# string reverse
puts str1.reverse # die demha

# bang method "!" - means overwrite what you have with the result
puts str1.reverse! #=> this band is the same as `str = str.reverse`

# include method
puts str1.include?("mo") # false .. check if a string is substring from another 

# empty & nill method
puts str1.empty? # check if string is empty
puts str1.slice(100, 4).nil? # check if string is nil
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>


# section 3 : Methods

### Define a method

```ruby
# define a method with default parameter
def test(par1, par2, default_par = 0)
  puts "parameter_1: #{par1}"
  puts "parameter_2: #{par2}"
  puts "default_parameter: #{default_par}"
end

test(24, "ahmed", "EGP")
```

### Return value

```ruby
# define method with return value
def return_sum_implicit(num1, num2)
  puts "this is Addition function"
  num1 + num2 # this is implicit return - by default ruby return the last valid expression
end

def return_sum_explicit(num1, num2)
  return num1 + num2 # this is explicit return using 'return' keyword
end
```

## `responde_to?`

<aside>
📌 `responde_to?` :*is a checker to check if a method is part of instance*

</aside>

```ruby
num = 10
num.respond_to?("next") # this will check if next is part of num
num.respond_to?(:next) # you can use symbol instead of string , it's a lightweight instead of string
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 4 : Conditions

### if

```ruby
name = "ahmed"

if name == "ahmed"
	puts "admin"
elsif name ="hassan"
	puts "user"
else
	puts "unknow"
end
```

### Ternary Operator

```ruby
number = 20
puts number > 15 ? true : false # true
```

### Case

```ruby
name = "ahmed"

case name
when "ahmed"
  puts "admin"
when "mohamed"
  puts "buyer"
when "hassan"
  puts "seller"
else
  puts "unKnown"
end
```

### case in range

```ruby
degree = 80

case degree
when 90..100
  puts "A+"
when 85..89
  puts "A"
when 75..84
  puts "B"
else
  puts "unKnown"
end

# print "B" 
```

### unless

<aside>
📌 `unless` : it’s another way to write if not

</aside>

```ruby
name = "ahmed"

if name != "ahmed"
	puts "unAuthorized"
end 

# you can do the same implementation using unless 

unless name == "ahmed" 
	puts "unAuthorized"
end
```

### while - until

```ruby
x = 1
while x < 10
	puts x
	x.next
end

# until means exucte until reach this condition 
# this example give us the same result as above
y = 1
until y > 9
	puts y
	y.next
end
```

### Inline modifier

<aside>
📌 In case our `if` condition consists of one line we can use Inline modifier.

</aside>

```ruby
number = 30 
if number > 25
 puts "hello"
end

# we can do the same using indline modifier 
puts "hello" if number > 25
```

### Conditional Assignments

<aside>
📌 assign a value if exists if not assign the default

</aside>

```ruby
letter ||= "Notification" # it's look like letter = letter || "Notification"
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 5 : Ranges

### create range using `..`

```ruby
num = 1..5 # this will assign an array start from [1,..,5]
puts num.first # 1 ... print the first number in the range 
puts num.last # 5 ... print the last number in the range 
puts num.first(4) # [1,2,3,4] ... print he first 4 number in the range
puts num.include?(3) # true ... check if the number 3 included or not in the range  
```

### Random

```ruby
puts rand # rand return a random number from 0 to 1
puts rand(0..100) # generate a random number in the range between 0 to 100
```

# section 6 : Arrays

### A shorthand way to write array of string

```ruby
name = %w[ahmed mahmoud eid] # name = ["ahmed", "mahmoud", "eid"] ,,, as you notice i didn't need to use double quotes or sperate each element with ,
```

### Create an array using `Array` class

```ruby
nil_array = Array.new(5) # nil_array = [nil, nil, nil, nil, nil] this will create array of length 5 will nill  values
puts nil_array 

default_array = Array.new(3,"default value") # default_array = ["default value", "default value", "default value"] , this will create array of length 3 with default value
puts default_array
```

### Accessing array with fetch

<aside>
📌 `fetch` method : is a way to access the array elements same as brackets `[]` , but the only difference `fetch`  can return default value in case not found

</aside>

```ruby
name = ["ahmed" , "mahmoud", "eid"]
puts name.fetch(1) # "mahmoud"
puts name.fetch(3, "Not found") # Not found 
```

### Accessing array using range and extractor

```ruby
fruits = ["Apple", "Orange", "Banana", "watermelon", "blah blah"]
puts fruits[1, 2] # will start from index 1 and reach index + 2
puts fruits.slice(1, 2) # same as above

puts fruits[1..4] # will start from index 1 to index 4
puts fruits.slice(1..4) # same as above
```

### Accessing element using `value_at`

<aside>
📌 `value_at` : returning an array containing the passed index , in case the index not found will return `nil`

</aside>

```ruby
fruits = ["Apple", "Orange", "Banana", "watermelon", "blah blah"]

puts fruits.values_at(0, 4, 2) # return ["Apple", "blah blah", "Orange"]
puts fruits.value_at(0, 6, 4) # return ["Apple",nil,4] ,,, note it return nil for not found index 
```

### Overwrite an array

```ruby
fruits = ["Apple", "Orange", "Banana", "watermelon", "blah blah"]

fruits[0] = "Tomato" # classic way to overwrite an array

fruits[0..3] = ["Cantaloupe", "Guava", "Mango"] # overwrite an array in a specific range

fruits[0..3] = ["Mango"] # ["Mango", "watermelon", "blah blah"] ,,, note I specified the range for 3 item by I passed only one value so the other two will deleted
```

### `count` method

<aside>
📌 *`count` : is same as `length` and `size` methods , the only difference it can count the repeat of a specific value*

</aside>

```ruby
number = [1, 2, 3, 2, 4, 5]

puts number.count
puts number.count(2) # will count how many times count repeated
```

### Adding to array

```ruby
number.push(6) # push: adding to end
number << 7 # << : shuffle operator same as push
number << 8 << 9 # you can push multiple item with shuffle
number.unshift(0) # unshift: adding the front
```

### Remove from array

```ruby
number.pop
number.pop(1) # 
number.shift
number.shift(1) # same with pop parameters
```

<aside>
👀 The different between pop with parameters `arr.pop(1)` and pop without `arr.pop` is pop parameters  return the removed items but pop without parameter it'll not return anything

</aside>

### Arrays equality and comparison

<aside>
📌 *equality* comparison between arrays *check the value and the **position** of this **value***

</aside>

```ruby
puts [1, 2, 3] == [1, 3, 2] # false because equality check the value and the position of this value
puts [1, 2, 3] == [1, 2, 3] #true
```

### Spaceship operator  `<=>`

<aside>
📌 Spaceship operator  `<=>` : is an operator to comparison it return o or -1 or 1 
`value1 <=> value2` 
*return -1 if value1 < value2
return 1 if value1 > value2
return 0 if the values are equal*

</aside>

```ruby
puts 4 <=> 5 # -1 ... return -1 if value1 < value2
puts 8 <=> 5 # 1 ... return 1 if value1 > value2
puts 5 <=> 5 # 0 ... return 0 if the values are equal
```

<aside>
📌 *we can take advantage of spaceship operator to the arrays comparison 
Because it will compare every element until found unequal values then apply spaceship rule ... if not then return 0 which mean they are equal*

</aside>

### `is_a?(data type)` method

<aside>
📌 *a method to check the value instance of the passed data type*

</aside>

```ruby
puts 1.is_a?(Fixnum) # true
puts 1.is_a?(Class) # false
puts number.is_a?(Array) # true
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 7 : Arrays with iteration

### .each

```ruby
numbers = [10,20,30,40,50]

number.each do |num|
 puts num
end
```

### for..in

```ruby
# for loop
numbers = [10,20,30,40,50]

for num in numbers 
  puts num
end

puts num #50 ,,, for loop variable is global 
```

<aside>
📌 The difference between `each` and `for-in` is for loop variable is global variable while each is a local

</aside>

### .each_with_index

> iterate over element and it's index
> 

```ruby
numbers.each_with_index do |element, index|
  puts "numbers[#{index}] : #{element}"
end
```

### .map & .collect

> `map` and `collect` are the same 
Both of them apply an operation for each element in the array and return the result in for of array
> 

```ruby
numbers = [1, 2, 3, 4]
sqrt = numbers.map do |num| # map each element in the array and return it squre root
  num * num
end

puts sqrt
```

### break key-word

> `break` : break iteration execution
> 

```ruby
10.times do |count| #=> break the iteration when the count==5
  break if count == 5
  puts count
end
```

### next key word

> `next` : skip the execution of the iteration at condition
> 

### .reverse

```ruby
numbers = [1, 2, 3, 4, 5]
numbers.reverse! # this will reverse the array and assign the reverse result to number ... numbers = number.reverse
puts numbers
```

### .sort

```ruby
# .sort method: sort the array
grade = [20, 10, 30, 50, 40]
grade.sort!
puts grade # print the sorted array
```

### concat

> you can use `concat` and `+` to concat to arrays
> 

```ruby
arr1 = ["ahmed", "mahmoud", "eid"]
arr2 = ["hassan", "wael", "elsaied"]

arr1 = arr1 + arr2
arr1.concat(arr2) # as you may note arr1 assign the result to first argument
puts arr1
```

### .max & .min

```ruby
grades = [20, 10, 30, 50, 40]
puts grade.max
puts grade.min
puts grade.max(2) # return the maximum two numbers
```

### .include?

> check if a specific value is exist on the array or not
> 

```ruby
name = ["moahmed", "ahmed", "hassan"]
name.include?("wael") # false ,,, check if the wael is exist or not
```

### .index

> `index` : get index of value in the array
> 

```ruby
name = ["moahmed", "ahmed", "hassan"]
name.index("ahmed") # 1 ,,, return the index of ahmed
```

### .unpack

> unpacking array means extract values from array
> 

```ruby
ahmed, mohamed, karrem = [["ahmed", 24, "egy"], ["mohamed", 39, "usa"], ["kareem", 23, "uae"]]
# this will assign 1st array to ahmed var and 2nd to mohamed and 3rd to krrem
puts ahmed, mohamed, karrem
```

### .select & .reject & .partition

<aside>
📌 All of them used for filtering
`select` : return all element that match specific condition.
`reject` :  remove all the element that match a specific condition.
`parition` :  do the same job of both select and reject at one call.

</aside>

```ruby
numbers = 1..20
even = numbers.select { |num| num.even? } # return all the event number

names = ["ahmed mahmoud", "mohamed mahmoud", "ahmed hassan", "mohamed hassan"]
remove_hassan = names.reject { |name| name.include?("hassan") } # this will remove all names which contain hassan
puts remove_hassan

numbers = 1..20
event, odd = numbers.partition { |num| num.even? } # even return two arrays , the first is one who do the job of select the second is one of reject method

puts "even numbers"
puts even

puts "odd numbers"
puts odd

```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 8: Strings

### Split

<aside>
📌 `split` a string into array based on a specific delimiter or condition

</aside>

```ruby
# .split(delimiter)
str = "ahmed mahmoud eid"
puts str.split # ["ahmed","mahmoud","eid"] the default split delimter is " " space
puts str.split("m") # ["ah", "ed", "ah","oud","eid"]
```

### each_char & chars

<aside>
📌 `each_char` : iterate over string character by character
`chars` : return array of string characters

</aside>

```ruby
gree = "Hello"
str.each_char do |char|
  puts char
end

puts "ahmed".chars
```

### Join

<aside>
📌 `join` : **convert an array to string

</aside>

```ruby
name_array = ["ahmed", "mahmoud", "eid"]
puts name_array.join # "ahmedmahmoudeid"
puts name_array.join("-") # "ahmed-mahmoud-eid" between each element place "-"
```

### Index & Rindex

<aside>
📌 get the `index` of character in string , `rindex` get the last index

</aside>

```ruby
name = "ahmed mahmoud"
puts name.index("d") # return "4"
puts name.rindex("d") # return "12"
```

### Insert

<aside>
📌 `insert(index,”str”):` insert at `index` the `str`

</aside>

```ruby
name = "ad"
name.insert(1, "hme") #"ahmed" ,,, name = "ahmed"
```

### S*equeeze*

<aside>
📌 `sequeeze` : remove the repetition of character in a raw … aahmed mmahmooud eiid ⇒ ahmed mahmoud eid

</aside>

```ruby
str = "aahmedd mahmooud"
puts str.squeeze # remove all repeted characters in  a raw
puts str.squeeze("a") # remove only repeated "a" in a raw ... squezze only the a
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 9: Array Bonus

### Object Pointers and Object Copies

<aside>
📌 In Ruby, arrays are objects, which means that when an array is assigned to a variable, the variable is actually pointing to the array object in memory. Assigning an array to a new variable does not create a new copy of the array, but rather creates a new pointer to the same array object.

</aside>

```ruby
array1 = [1, 2, 3]
array2 = array1

array2 << 4

puts array1 # [1, 2, 3, 4]
puts array2 # [1, 2, 3, 4]

```

To create a new copy of an array, you can use the `dup` method.

```ruby
array1 = [1, 2, 3]
array2 = array1.dup

array2 << 4

puts array1 # [1, 2, 3]
puts array2 # [1, 2, 3, 4]

```

### Splat Arguments

Splat arguments allow you to pass an array as arguments to a method. In the method definition, the splat operator (`*`) is used to collect the arguments into an array.

```ruby
def print_numbers(*numbers)
  numbers.each { |num| puts num }
end

numbers = [1, 2, 3, 4]
print_numbers(*numbers) # pass array as arguments using * operator

```

### .any & .all

The `any?` and `all?` methods are used to check if any or all elements in an array meet a certain condition.

```ruby
array = [1, 2, 3, 4]

puts array.any? { |num| num > 3 } # true
puts array.all? { |num| num > 3 } # false

```

### .find

The `find` method is used to find the first element in an array that meets a certain condition.

```ruby
array = [1, 2, 3, 4]

puts array.find { |num| num > 2 } # 3

```

### .uniq

The `uniq` method is used to remove duplicate elements from an array.

```ruby
array = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]

puts array.uniq # [1, 2, 3, 4]

```

### .compact

The `compact` method is used to remove `nil` values from an array.

```ruby
array = [1, nil, 2, nil, 3, nil]

puts array.compact # [1, 2, 3]

```

### .inject & .reduce

The `inject` and `reduce` methods are used to aggregate the elements in an array into a single value. The method takes an initial value and a block, and the block is executed for each element in the array.

```ruby
array = [1, 2, 3, 4]

puts array.inject(0) { |sum, num| sum + num } # 10
puts array.reduce(1) { |product, num| product * num } # 24

```

### .flatten

The `flatten` method is used to transform a multi-dimensional array into a one-dimensional array.

```ruby
array = [1, [2, 3], [4, [5, 6]]]

puts array.flatten # [1, 2, 3, 4, 5, 6]

```

### .zip

`.zip` is used to combine two or more arrays into a single array of arrays, where each sub-array contains the corresponding elements from each of the original arrays.

```ruby
arr1 = [1, 2, 3]
arr2 = ['a', 'b', 'c']
arr3 = ['x', 'y', 'z']

arr4 = arr1.zip(arr2, arr3)
p arr4 # [[1, "a", "x"], [2, "b", "y"], [3, "c", "z"]]

```

### .sample

`.sample` is used to return a random element from an array.

```ruby
arr = [1, 2, 3, 4, 5]
p arr.sample # returns a random element from the array

```

### Array Union `|`

`|` is used to return a new array that contains all elements from both arrays, with duplicates removed.

```ruby
arr1 = [1, 2, 3]
arr2 = [2, 3, 4]

arr3 = arr1 | arr2
p arr3 # [1, 2, 3, 4]

```

### Array Difference ``

- `` is used to return a new array that contains all elements from the first array that are not in the second array.

```ruby
arr1 = [1, 2, 3]
arr2 = [2, 3, 4]

arr3 = arr1 - arr2
p arr3 # [1]

```

### Array Intersection `&`

`&` is used to return a new array that contains only the elements that are common to both arrays.

```ruby
arr1 = [1, 2, 3]
arr2 = [2, 3, 4]

arr3 = arr1 & arr2
p arr3 # [2, 3]

```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 10: Hashes

## Hashes in Ruby

<aside>
📌 A hash, also known as a dictionary or associative array, is a collection of key-value pairs where each key is unique. In Ruby, hashes are unordered.

</aside>

## Creating a Hash

<aside>
📌 You can create a hash in Ruby by using curly braces `{}` or the `Hash.new` constructor. Here's an example of creating a hash using both a string and a symbol as keys:

</aside>

```ruby
# Using string as key
hash_string = { "name" => "John", "age" => 30 }

# Using symbol as key
hash_symbol = { name: "John", age: 30 }

```

## Symbols in Ruby

<aside>
🔥 - A symbol in Ruby is an immutable identifier. It starts with a colon (`:`) followed by a name. 
- Symbols are often used as keys in hashes because they are more memory-efficient than strings and can improve performance when used as identifiers. Unlike strings, symbols are not garbage collected.

</aside>

```ruby
# Using symbol as key
person = { name: "John", age: 30 }

```

## Accessing Hash Properties

<aside>
📌 - You can access hash properties using square brackets `[]` or the `fetch` method.
- Square brackets return `nil` if the key is not found, while `fetch` allows you to specify a default value to be returned instead.

</aside>

```ruby
person = { name: "John", age: 30 }

# Accessing using square brackets
person[:name]  # Output: "John"

# Accessing using fetch
person.fetch(:name)  # Output: "John"
person.fetch(:country, "Unknown")  # Output: "Unknown"

```

## Adding a Key to a Hash

<aside>
📌 To add a new key-value pair to a hash, you can use the assignment operator (`=`) or the `store` method.

</aside>

```ruby
person = { name: "John", age: 30 }

# Adding a new key-value pair
person[:country] = "USA"

# Using store method
person.store(:city, "New York")

```

## Length and Empty

<aside>
📌 You can use the `length` method to get the number of key-value pairs in a hash, and the `empty?` method to check if a hash is empty.

</aside>

```ruby
person = { name: "John", age: 30 }

person.length  # Output: 2
person.empty?  # Output: false

```

## Iterating over a Hash

<aside>
📌 You can use the `each` method to iterate over a hash. It provides two different block argument formats: `|key, value|` and `|pair|`.

</aside>

```ruby
person = { name: "John", age: 30 }

# Iterating with |key, value|
person.each do |key, value|
  puts "#{key}: #{value}"
end

# Iterating with |pair|
person.each do |pair|
  key, value = pair
  puts "#{key}: #{value}"
end

```

## Iterating over Keys and Values

<aside>
📌 You can use the `each_key` and `each_value` methods to iterate over just the keys or values of a hash, respectively.

</aside>

```ruby
person = { name: "John", age: 30 }

# Iterating over keys
person.each_key do |key|
  puts key
end

# Iterating over values
person.each_value do |value|
  puts value
end

```

## Retrieving Keys and Values

<aside>
📌 To retrieve all the keys or values of a hash as an array, you can use the `keys` and `values` methods, respectively.

</aside>

```ruby
person = { name: "John", age: 30 }

keys_array = person.keys
values_array = person.values

puts keys_array.inspect  # Output: [:name, :age]
puts values_array.inspect  # Output: ["John", 30]

```

## Converting Hash to Array and Vice Versa

<aside>
📌 You can convert a hash to an array using the `to_a` method, which returns an array of key-value pairs. To convert an array of key-value pairs back to a hash, you can use the `to_h` method.

</aside>

```ruby
person = { name: "John", age: 30 }

# Converting hash to array
array = person.to_a
puts array.inspect  # Output: [[:name, "John"], [:age, 30]]

# Converting array to hash
hash = array.to_h
puts hash.inspect  # Output: {:name=>"John", :age=>30}

```

## Sorting a Hash

<aside>
📌 You can sort a hash based on its keys using the `sort` method or based on custom criteria using the `sort_by` method.

</aside>

```ruby
person = { name: "John", age: 30, country: "USA" }

# Sorting by keys
sorted_hash =person.sort.to_h
puts sorted_hash.inspect  # Output: {:age=>30, :country=>"USA", :name=>"John"}

# Sorting by custom criteria (e.g., value length)
sorted_hash = person.sort_by { |key, value| value.length }.to_h
puts sorted_hash.inspect  # Output: {:name=>"John", :age=>30, :country=>"USA"}

```

## Deleting a Key from a Hash

<aside>
📌 You can delete a key-value pair from a hash using the `delete` method. This method returns the value associated with the deleted key, or `nil` if the key is not found.

</aside>

```ruby
person = { name: "John", age: 30 }

deleted_value = person.delete(:name)
puts deleted_value  # Output: "John"
puts person.inspect  # Output: {:age=>30}

```

## Selecting and Rejecting Hash Elements

<aside>
📌 You can select specific key-value pairs from a hash based on a condition using the `select` method. Similarly, you can reject key-value pairs based on a condition using the `reject` method.

</aside>

```ruby
person = { name: "John", age: 30, country: "USA" }

# Selecting key-value pairs based on condition
selected_hash = person.select { |key, value| value.is_a?(String) }
puts selected_hash.inspect  # Output: {:name=>"John", :country=>"USA"}

# Rejecting key-value pairs based on condition
rejected_hash = person.reject { |key, value| value.is_a?(String) }
puts rejected_hash.inspect  # Output: {:age=>30}

```

## Merging Hashes

<aside>
📌 You can merge two hashes together using the `merge` method. If a key already exists in the original hash, the value from the merged hash will overwrite it.

</aside>

```ruby
person = { name: "John", age: 30 }
additional_info = { country: "USA", occupation: "Engineer" }

merged_hash = person.merge(additional_info)
puts merged_hash.inspect  # Output: {:name=>"John", :age=>30, :country=>"USA", :occupation=>"Engineer"}

```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 11: Ruby Blocks, Procs, and Lambdas

## Blocks

### What is a block?

A block is a piece of code in Ruby that can be passed to methods as an argument. It is a way to group statements together and is often used for iteration or to define small, reusable pieces of code.

```ruby
# yield
def pass_control
  puts "Before block calling"
  yield # will pass the control from the method to the block
  puts "After block calling"
end

pass_control { puts "Execute the block" }

```

Output:

```
Before block calling
Execute the block
After block calling

```

### `yield` keyword and its use to transfer control to the block

The `yield` keyword is used to transfer control from a method to a block. When a method encounters a `yield` statement, it executes the code within the associated block.

### Assigning block return to a variable using `yield`

You can assign the return value of a block to a variable using the `yield` keyword.

```ruby
# block return
def block_return
  name = yield # assign the return of the block to the name
  puts "Welcome #{name}"
end

block_return { "Ahmed" } # with a block, we don't use the return keyword to return something

```

Output:

```
Welcome Ahmed

```

### Calling `yield` multiple times

A method can call `yield` multiple times to execute the block multiple times.

```ruby
# you can call yield multiple times
def multiple_yield
  yield
  puts "break"
  yield
end

multiple_yield { puts "This is a block" }

```

Output:

```
This is a block
break
This is a block

```

## Procs

### What is a proc?

A proc is a saved block of code that can be reused. It is an object in Ruby that represents a block.

```ruby
# proc: is a saved block that you can use multiple times
cubes = Proc.new { |number| number ** 3 } # define a proc to use
a = [1, 2, 3, 4]
b = [5, 6, 7, 8]

a_cube = a.map(&cubes) # to use a defined proc, you should use the "&" operator
b_cube = b.map(&cubes)

```

### Using a defined proc and passing it using `&`

You can use a defined proc by passing it to a method using the `&` symbol.

### `block_given?` method

The `block_given?` method is used to check if a block has been passed to a method. It returns `true` if a block is given and `false` otherwise.

### `proc.call` method usage: allowing to call the proc directly

The `call` method is used to invoke a proc and execute the code within it.

### Using a Ruby method as a proc

You can pass a Ruby method as a proc using the `&` symbol. This is a shorthand way to convert a method into a proc.

### Method with a proc parameter

You can define a method that takes a proc as a parameter and invoke the proc within the method.

## Lambdas

### What is a lambda and its usage

A lambda is a type of proc in Ruby. It is an anonymous function that can be assigned to a variable or passed as an argument to a method.

```ruby
# Lambda
## Define:
my_lambda = lambda { |name| puts "Hello, #{name}!" }
my_lambda.call("Bob")

```

Output:

```
Hello, Bob!

```

### Difference between proc and lambda and their return behavior

The main differences between procs and lambdas are:

1. Return behavior: A `return` statement inside a lambda will only return from the lambda itself, while a `return` statement inside a proc will also return from the enclosing method.

Example with lambda:

```ruby
def lambda_example
  my_lambda = lambda { return "Hello" }
  my_lambda.call
  puts "World"
end

lambda_example

```

Output:

```
Hello

```

Example with proc:

```ruby
def proc_example
  my_proc = proc { return "Hello" }
  my_proc.call
  puts "World"
end

proc_example

```

Output:

```
Hello

```

The `puts "World"` line is not executed in the proc example because the `return` statement in the proc terminates the method.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 12: Classes

## Definition and Object Creation

```ruby
class MyClass
  # Class code here
end

obj = MyClass.new

```

- To define a class in Ruby, use the `class` keyword followed by the class name.
- Inside the class, you can define methods and variables specific to that class.
- To create an object of a class, use the `new` method.

## Class Methods and Ancestors

```ruby
obj.methods
obj.ancestors

```

- The `methods` method returns a list of all the methods available for the object.
- The `ancestors` method returns a list of all the classes and modules that the object inherits from.

## Type Checking

```ruby
obj.is_a?(MyClass)

```

- The `is_a?` method checks if an object is an instance of a specific class.

## Method Existence Check

```ruby
obj.respond_to?(:method_name)

```

- The `respond_to?` method checks if an object responds to a particular method.

## Object ID

```ruby
obj.object_id

```

- The `object_id` method returns a unique identifier for the object.

## Instance Variables

```ruby
class MyClass
  def initialize
    @instance_var = 42
  end
end

obj = MyClass.new
obj.instance_variables

```

- Instance variables are prefixed with `@` and are accessible throughout the class.
- The `instance_variables` method returns a list of all the instance variables defined for an object.

## Initialize Method

```ruby
class MyClass
  def initialize(arg1, arg2)
    @arg1 = arg1
    @arg2 = arg2
  end
end

obj = MyClass.new(value1, value2)

```

- The `initialize` method is a special method that is automatically called when an object is created using the `new` method.
- It is used to initialize the object with any necessary values.

## Self Keyword

```ruby
class MyClass
  def method1
    puts self
  end
end

obj = MyClass.new
obj.method1

```

- The `self` keyword refers to the current object.
- Inside an instance method, `self` refers to the instance of the class on which the method is called.

## Encapsulation and Getter/Setter

```ruby
class MyClass
  def initialize
    @value = 42
  end

  def value
    @value
  end

  def value=(new_value)
    @value = new_value
  end
end

obj = MyClass.new
obj.value
obj.value = 24

```

- Encapsulation is the practice of hiding the internal details of an object and providing controlled access to them.
- Getter methods are used to retrieve the value of an instance variable, while setter methods are used to set or modify the value.

## Shortcut Attr for Getter/Setter

```ruby
class MyClass
  attr_accessor :value

  def initialize
    @value = 42
  end
end

obj = MyClass.new
obj.value
obj.value = 24

```

- Ruby provides a shortcut using the `attr_accessor` method to automatically create getter and setter methods for an instance variable.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 13: Module

## Definition and Inclusion

```ruby
module MyModule
  # Module code here
end

class MyClass
  include MyModule
end

obj = MyClass.new

```

- A module in Ruby is a collection of methods, constants, and other module or class definitions.
- Modules are used to group related functionality and provide a way to share code between classes.
- The `include` keyword is used to include a module in a class.

## Difference between Module and Class

- A class can be instantiated to create objects, while a module cannot.
- A class can inherit from another class, but a module cannot inherit from or be inherited by another module or class.
- Modules are used to share functionality among classes through inclusion.

## Import Module

```ruby
require_relative 'path/to/module_file'

```

- The `require_relative` statement is used to import a module from a specific file location.

## Mixins and Method Hierarchy

```ruby
module MixinModule
  def my_method
    puts "Mixin Module Method"
  end
end

class MyClass
  include MixinModule

  def my_method
    puts "Class Method"
    super
  end
end

obj = MyClass.new
obj.my_method

```

- Mixins are a way to add methods from a module to a class.
- When a class includes a module, the methods defined in the module become available to instances of the class.
- If a method with the same name exists in both the class and the module, the class method takes precedence.
- The `superkeyword is used to call the superclass implementation of a method.

## Prepend and Extend

```ruby
module PrependModule
  def my_method
    puts "Prepend Module Method"
    super
  end
end

module ExtendModule
  def my_method
    puts "Extend Module Method"
    super
  end
end

class MyClass
  prepend PrependModule
  extend ExtendModule

  def my_method
    puts "Class Method"
  end
end

obj = MyClass.new
obj.my_method
MyClass.my_method

```

- The `prepend` keyword is used to prepend a module to the method lookup chain of a class.
- When a module is prepended to a class, its methods take precedence over the class methods.
- The `extend` keyword is used to extend a class with module methods.
- When a class extends a module, the module methods become available at the class level.

## Enumerable Module

```ruby
class MyCollection
  include Enumerable

  def initialize
    @items = []
  end

  def <<(item)
    @items << item
  end

  def each
    @items.each { |item| yield item }
  end
end

collection = MyCollection.new
collection << 1
collection << 2
collection << 3

collection.each { |item| puts item }
collection.map { |item| item * 2 }

```

- The `Enumerable` module provides a set of methods for working with collections, such as arrays, hashes, and custom collection classes.
- To make a class enumerable, include the `Enumerable` module and define an `each` method that yields each item in the collection.
- The `each` method is required by the `Enumerable` module and should iterate over the collection and yield each item to a block.
- Once a class is made enumerable, you can use methods like `each`, `mapselect`, and more on instances of that class.



<p align="right">(<a href="#readme-top">back to top</a>)</p>

# section 14: Classes ||

## Private Method and How to Use Them

- Private methods in Ruby can only be called within the context of the defining class or module and cannot be called with an explicit receiver.
- To define a private method, use the `private` keyword followed by the method name.
- Private methods are typically used to encapsulate implementation details and are not intended to be called directly from outside the class.

```ruby
class MyClass
  def public_method
    puts "This is a public method"
    private_method  # Private method can be called within the class
  end

  private

  def private_method
    puts "This is a private method"
  end
end

my_object = MyClass.new
my_object.public_method
```

## Protected Methods

- Protected methods in Ruby can be called by any instance of the defining class or its subclasses.
- Protected methods can be called with an explicit receiver and can also be accessed from within other instances of the same class or its subclasses.
- To define a protected method, use the `protected` keyword followed by the method name.

```ruby
class MyClass
  def public_method
    puts "This is a public method"
    protected_method  # Protected method can be called within the class
  end

  protected

  def protected_method
    puts "This is a protected method"
  end
end

my_object = MyClass.new
my_object.public_method
```

## Difference Between Protected and Private Methods

- The main difference between protected and private methods is the accessibility.
- Protected methods can be called by any instance of the class or its subclasses, while private methods can only be called within the defining class or module.
- Protected methods can be accessed with an explicit receiver, whereas private methods cannot.

```ruby
class MyClass
  def public_method
    puts "This is a public method"
    protected_method  # Can access protected method because it's within the class
    private_method  # Cannot access private method because it's within the class
  end

  protected

  def protected_method
    puts "This is a protected method"
  end

  private

  def private_method
    puts "This is a private method"
  end
end

my_object = MyClass.new
my_object.public_method
```

## Instance Methods vs. Instance Variables in a Class

- Instance methods in a class define the behavior of objects created from that class. They encapsulate the operations or actions that objects can perform.
- Instance variables, on the other hand, store the state or data of each individual object. They hold the values unique to each object.
- It is generally considered good practice to define instance methods to operate on instance variables rather than directly accessing or modifying the instance variables from outside the class.

```ruby
class MyClass
  def initialize(name)
    @name = name  # Instance variable to store the name
  end

  def greet
    puts "Hello, #{@name}!"  # Instance method accessing the instance variable
  end
end

my_object = MyClass.new("John")
my_object.greet  # Outputs "Hello, John!"
```

### Struct and How to Implement It

- A struct in Ruby is a lightweight data structure that acts as a container for storing and accessing multiple attributes.
- It provides a way to bundle related data together without defining a full-fledged class.
- To define a struct, use the `Struct` keyword followed by the desired struct name and a list of attribute names.
- Example:

```ruby
Person = Struct.new(:name, :age)
person = Person.new("John", 30)
puts person.name
puts person.age

```

### Difference Between Struct and Class

- A struct is a lightweight data structure that mainly focuses on bundling related data together.
- A class is a more general-purpose construct in Ruby that can define behavior (methods) and state (instance variables) in addition to bundling data.
- Classes provide more flexibility and customization options compared to structs.

### Monkey Patching

- Monkey patching in Ruby refers to modifying or extending existing classes or modules during runtime.
- It allows you to add, modify, or remove methods and attributes from existing classes or modules.
- Monkey patching can be useful in situations where you want to add functionality to existing classes or fix bugs without modifying the original source code.
- However, it should be used with caution to avoid conflicts and unintended consequences.

### Examples of Monkey Patching

- Adding a new method to an existing class:

```ruby
class String
  def shout
    self.upcase + "!"
  end
end

puts "hello".shout # Outputs "HELLO!"

```

- Modifying an existing method of a class:

```ruby
class Array
  def sum
    reduce(:+)
  end
end

puts [1, 2, 3, 4, 5].sum # Outputs 15

```

### Class Variables and Class Methods

- Class variables in Ruby are shared among all instances of a class and are prefixed with `@@`.
- They are accessible within the class and its subclasses.
- Class methods, on the other hand, are methods that are defined on the class itself rather than on instances of the class.
- Class variables and methods are accessed using the class name itself.
- Example:

```ruby
class MyClass
  @@class_var = 42

  def self.class_var
    @@class_var
  end
end

puts MyClass.class_var # Outputs 42

```

### Inheritance Hierarchy

- To check the inheritance hierarchy of a class, you can use the `<` operator:

```ruby
class SubClass < SuperClass
  # Class code here
end

```

- The `<` operator indicates that `SubClass` inherits from `SuperClass`.
- The inheritance hierarchy determines the order in which methods are looked up and resolved.

### Difference Between `is_a?` and `instance_of?`

- The `is_a?` method checks if an object is an instance of a specific class or its subclasses.
- The `instance_of?` method checks if an object is an instance of a specific class only, excluding its subclasses.

```ruby
class MyClass; end
class MySubClass < MyClass; end

object = MySubClass.new

puts object.is_a?(MyClass)  # Returns true because MySubClass is a subclass of MyClass
puts object.instance_of?(MyClass)  # Returns false because MySubClass is not an instance of MyClass
```

### Method Overriding in Subclasses

- Method overriding in Ruby allows a subclass to provide its own implementation of a method that is already defined in its superclass.
- The overridden method in the subclass takes precedence over the superclass method when called on instances of the subclass.

```ruby
class Animal
  def speak
    puts "Animal speaks"
  end
end

class Cat < Animal
  def speak
    puts "Meow"
  end
end

animal = Animal.new
animal.speak  # Outputs "Animal speaks"

cat = Cat.new
cat.speak  # Outputs "Meow"
```

### `super` Keyword

The `super` keyword in Ruby is used to call a method with the same name in the superclass from within a subclass.

- It is often used in method overriding to invoke the superclass's implementation of a method before adding or modifying the behavior in the subclass.
- The `super` keyword can be used with parentheses, without parentheses, or with arguments to pass arguments to the superclass method.

```ruby
class Animal
  def speak
    puts "Animal speaks"
  end
end

class Cat < Animal
  def speak
    super
    puts "Meow"
  end
end

cat = Cat.new
cat.speak
# Outputs:
# "Animal speaks"
# "Meow"
```

- Example scenarios:
    - `super`: Calls the superclass method without passing any arguments.
    - `super()`: Calls the superclass method with empty parentheses, indicating no arguments are passed.
    - `super(argument)`: Calls the superclass method with the specified argument.

### Using Hashes within the Class Constructor

- In Ruby, you can use hashes within the class constructor to pass multiple arguments as named parameters.
- The hash can be accessed within the constructor to extract the values and assign them to instance variables.
- Example:

```ruby
class MyClass
  def initialize(details)
    @instance_1 = details[:age]
    @instance_2 = details[:name]
  end
end

my_object = MyClass.new({ age: 30, name: "John" })

```

### Empty Hash in Constructor and Its Advantages

- Defining an empty hash in the constructor allows you to provide default values for the parameters.
- This ensures that the constructor can be called without providing any arguments, and the default values will be used.
- It provides flexibility and avoids errors when some arguments are not provided.
- Example:

```ruby
class MyClass
  def initialize(details = {})
    @instance_1 = details[:age]
    @instance_2 = details[:name]
  end
end

my_object = MyClass.new  # No arguments provided, default values will be used

```

### Hashes with Default Values in Constructor

- You can define default values for the hash parameters in the constructor.
- This allows you to merge the provided details with the default values, ensuring that all required attributes have a value.
- Example:

```ruby
class MyClass
  def initialize(details = {})
    default = { age: 30, name: "user" }
    details = default.merge(details)
    @instance_1 = details[:age]
    @instance_2 = details[:name]
  end
end

my_object = MyClass.new({ name: "John" })  # Only name provided, age will use the default value

```
