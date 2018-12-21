# Practices

def foo(first, second, third, *therest):
    print("First: %s" %(first))
    print("Second: %s" %(second))
    print("Third: %s" %(third))
    print("And all the rest... %s" %(list(therest)))

foo(1,2,3,4,5)


def foo(first, second, third, fourth, fifth, sixth, seventh, *therest):
    print("First: %s" %(first))
    print("Second: %s" %(second))
    print("Third: %s" %(third))
    print("Fourth: %s" %(fourth))
    print("Fifth: %s" %(fifth))
    print("Sixth: %s" %(sixth))
    print("Seventh: %s" %(seventh))
    print("And all the rest...%s" %(list(therest)))
    
foo(1,2,3,4,5,6,7,8,9,10)

def bar(first, second, third, **options):
    if options.get("action") == "sum":
        print("The sum is: %d" %(first + second + third))

    if options.get("number") == "first":
        return first

result = bar(1, 3, 5, action = "sum", number = "first")
print("Result: %d" %(result))



    # edit the functions prototype and implementation
def foo(a, b, c, *args):
    return len(args)

def bar(a, b, c, **kwargs):
    return kwargs["magicnumber"] == 7


# test code
if foo(1,2,3,4) == 1:
    print("Good.")
if foo(1,2,3,4,5) == 2:
    print("Better.")
if bar(1,2,3,magicnumber = 6) == False:
    print("Great.")
if bar(1,2,3,magicnumber = 7) == True:
    print("Fantastic!")

# Exercise: make a regular expression that will match an email
import re
def test_email(your_pattern):
    pattern = re.compile(your_pattern)
    emails = ["john@example.com", "python-list@python.org", "wha.t.`1an?ug{}ly@email.com"]
    for email in emails:
        if not re.match(pattern, email):
            print("You failed to match %s" % (email))
        elif not your_pattern:
            print("Forgot to enter a pattern!")
        else:
            print("Pass")
# Your pattern here!
pattern = r"\"?([-a-zA-Z0-9.`?{}]+@\w+\.\w+)\"?"
test_email(pattern)

def do_stuff_with_number(n):
        print(n)

the_list = (1, 2, 3, 4, 5)

for i in range(20):
    try:
        do_stuff_with_number(the_list[i])
    except IndexError: # Raised when accessing a non-existing index of a list
        do_stuff_with_number(0)
        
def do_stuff_with_number(n):
    print(n)

the_list = (1, 2, 3, 4, 5)

for i in range(12):
    try:
        do_stuff_with_number(the_list[i])
    except IndexError: #Raised when accesing a non-existing index of a list
        do_stuff_with_number(0)
        
def do_stuff_with_number(n):
        print(n)

the_list = (1, 2, 3, 4, 5)

for i in range(20):
    try:
        do_stuff_with_number(the_list[i])
    except IndexError: # Raised when accessing a non-existing index of a list
        do_stuff_with_number(0)
        
a = set(["Jake", "John", "Eric"])
print(a)
b = set(["John", "Jill"])
print(b)

a = set(["Jake", "John", "Eric", "Jason"])
b = set(["John", "Jill", "Jake"])
A = set(a)
B = set(b)

print(A.difference(B))

import json
json_string = json.dumps([1, 2, 3, "a", "b", "c"])
print(json_string)

import pickle
pickled_string = pickle.dumps([1, 2, 3, "a", "b", "c"])
print(pickle.loads(pickled_string))

import json

# fix this function, so it adds the given name
# and salary pair to salaries_json, and return it
def add_employee(salaries_json, name, salary):
    salaries = json.loads(salaries_json)
    salaries[name] = salary

    return json.dumps(salaries)

# test code
salaries = '{"Alfred" : 300, "Jane" : 400 }'
new_salaries = add_employee(salaries, "Me", 800)
decoded_salaries = json.loads(new_salaries)
print(decoded_salaries["Alfred"])
print(decoded_salaries["Jane"])
print(decoded_salaries["Me"])

from functools import partial

def multiply(x,y):
        return x * y

# create a new function that multiplies by 2
dbl = partial(multiply,2)
print(dbl(4))

# Define the Vehicle class
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str

# Print a list of all attributes of the Vehicle class.
print(dir(Vehicle))

def multiplier_of(n):
    def multiplier(number):
        return number*n
    return multiplier

multiplywith5 = multiplier_of(7)
print(multiplywith5(8))


def multiplier_of(n):
    def multiplier(number):
        return number*n
    return multiplier

multiplierwith8 = multiplier_of(8)
print(multiplierwith8(2))

def divider_of(n):
    def divider(number):
        return number/n
    return divider

dividerbetween8 = divider_of(8)
print(dividerbetween8(4))


def type_check(correct_type):
    def check(old_function):
        def new_function(arg):
            if (isinstance(arg, correct_type)):
                return old_function(arg)
            else:
                print("Bad Type")
        return new_function
    return check

@type_check(int)
def times2(num):
    return num*2

print(times2(2))
times2('Not A Number')

@type_check(str)
def first_letter(word):
    return word[0]

print(first_letter('Bye World'))
first_letter(['Not', 'A', 'String'])

def type_check(correct_type):
    def check(old_function):
        def new_function(arg):
            if (isinstance(arg,correct_type)):
                return old_function(arg)
            else:
                print("Good People")
        return new_function
    return check

@type_check(int)
def times2(num):
    return num*2

print(times2(8))
times2("Not a winner")

@type_check(str)
def first_letter(word):
    return word[0]

print(first_letter("Juggernaut"))
first_letter(["Not", "A","String"])

def type_check(correct_type):
    def check(old_function):
        def new_function(arg):
            if (isinstance(arg,correct_type)):
                return old_function(arg)
            else:
                print("Good People")
        return new_function
    return check

@type_check(int)
def times2(num):
    return num*2

print(times2(10))
times2("Not a winner")

@type_check(str)
def first_letter(word):
    return word[0]

print(first_letter("Juggernaut"))
first_letter(["Not", "A","String"])
