# Python Coursera
#Python-Crash-Course

##Practice Notebook: Reading and Writing Files



##Question 1 

####In this exercise, we will test your knowledge of reading and writing files by playing around with some text files.

Let's say we have a text file containing current visitors at a hotel. We'll call it, guests.txt. Run the following code to create the file. The file will automatically populate with each initial guest's first name on its own line.

``` python
guests = open("guests.txt", "w")
initial_guests = ["Bob", "Andrea", "Manuel", "Polly", "Khalid"]

for i in initial_guests:
    guests.write(i + "\n")
    
guests.close()
```   

##Question 2 

####The output shows that our *guests.txt* file is correctly populated with each initial guest's first name on its own line.  Cool!

Now suppose we want to update our file as guests check in and out.  Fill in the missing code in the following cell to add guests to the *guests.txt* file as they check in.


``` python
new_guests = ["Sam", "Danielle", "Jacob"]

with open("guests.txt","a") as guests:
    for i in new_guests:
        guests.write(i + "\n")

guests.close()
```   


##Question 2 

####The current names in the *guests.txt* file should be:  Bob, Andrea, Manuel, Polly, Khalid, Sam, Danielle and Jacob.
<br><br>
Was the *guests.txt* file correctly appended with the new guests? If not, go back and edit your code making sure to fill in the gaps appropriately so that the new guests are correctly added to the *guests.txt* file.  Once the new guests are successfully added, you have filled in the missing code correctly.  Great!
<br><br>
Now let's remove the guests that have checked out already.  There are several ways to do this, however, the method we will choose for this exercise is outlined as follows:
1. Open the file in "read" mode.
2. Iterate over each line in the file and put each guest's name into a Python list.
3. Open the file once again in "write" mode.
4. Add each guest's name in the Python list to the file one by one.

<br>
Ready? Fill in the missing code in the following cell to remove the guests that have checked out already.

``` python
checked_out=["Andrea", "Manuel", "Khalid"]
temp_list=[]

with open("guests.txt", "r") as guests:
    for g in guests:
        temp_list.append(g.strip())

with open("guests.txt", "w") as guests:
    for name in temp_list:
        if name not in checked_out:
            guests.write(name + "\n")
```   

## C2M2L1_Reading_And_Writing_Files

####The current names in the guests.txt file should be: Bob, Polly, Sam, Danielle and Jacob.

Were the names of the checked out guests correctly removed from the guests.txt file? If not, go back and edit your code making sure to fill in the gaps appropriately so that the checked out guests are correctly removed from the guests.txt file. Once the checked out guests are successfully removed, you have filled in the missing code correctly. Awesome!

Now let's check whether Bob and Andrea are still checked in. How could we do this? We'll just read through each line in the file to see if their name is in there. Run the following code to check whether Bob and Andrea are still checked in.
To represent the servers that are taking care of the connections, we'll use a Server class. Each connection is represented by an id, that could, for example, be the IP address of the computer connecting to the server. For our simulation, each connection creates a random amount of load in the server, between 1 and 10.

Run the following code that defines this Server class.

``` python
guests_to_check = ['Bob', 'Andrea']
checked_in = []

with open("guests.txt","r") as guests:
    for g in guests:
        checked_in.append(g.strip())
    for check in guests_to_check:
        if check in checked_in:
            print("{} is checked in".format(check))
        else:
            print("{} is not checked in".format(check))

```   

## Practice Quiz: Managing Files & Directories




Question 1
The create_python_script function creates a new python script in the current working directory, adds the line of comments to it declared  by the 'comments' variable, and returns the size of the new file. Fill in the gaps to create a script called "program.py".

``` python
import os
def create_python_script(filename):
  comments = "# Start of a new Python program"
  with open(filename, 'w') as file: 
    filesize =os.path.getsize(filename)
  return(filesize)


print(create_python_script("program.py"))

```   

Question 1
The create_python_script function creates a new python script in the current working directory, adds the line of comments to it declared  by the 'comments' variable, and returns the size of the new file. Fill in the gaps to create a script called "program.py".

``` python
import os

def new_directory(directory, filename):
  # Before creating a new directory, check to see if it already exists
  if os.path.isdir(directory) == False:
     os.makedirs(directory, exist_ok=True)

  # Create the new file inside of the new directory
  os.chdir(directory)
  with open (filename,"w") as file:
    pass

  os.chdir("..")
  # Return the list of files in the new directory
  return os.listdir(directory)

print(new_directory("PythonPrograms", "script.py"))

```  


Question 1
#Reading & Writing CSV Files
We're working with a list of flowers and some information about each one. The create_file function writes this information to a CSV file. The contents_of_file function reads this file into records and returns the information in a nicely formatted block. Fill in the gaps of the contents_of_file function to turn the data in the CSV file into a dictionary using DictReader.
``` python
import os
import csv

# Create a file with data in it
def create_file(filename):
  with open(filename, "w") as file:
    file.write("name,color,type\n")
    file.write("carnation,pink,annual\n")
    file.write("daffodil,yellow,perennial\n")
    file.write("iris,blue,perennial\n")
    file.write("poinsettia,red,perennial\n")
    file.write("sunflower,yellow,annual\n")

# Read the file contents and format the information about each row
def contents_of_file(filename):
  return_string = ""

  # Call the function to create the file 
  create_file(filename)

  #Open the file
  with open(filename) as file:
    # Read the rows of the file into a dictionary
    f = csv.DictReader(file)
    # Process each item of the dictionary
    for row in f:
      return_string += "a {} {} is {}\n".format(row["color"], row["name"], row["type"])
  return return_string
#Call the function
print(contents_of_file("flowers.csv"))

```   

Question 2
#Reading & Writing CSV Files
 Using the CSV file of flowers again, fill in the gaps of the contents_of_file function to process the data without turning it into a dictionary. How do you skip over the header record with the field names?

``` python
import os
import csv

# Create a file with data in it
def create_file(filename):
  with open(filename, "w") as file:
    file.write("name,color,type\n")
    file.write("carnation,pink,annual\n")
    file.write("daffodil,yellow,perennial\n")
    file.write("iris,blue,perennial\n")
    file.write("poinsettia,red,perennial\n")
    file.write("sunflower,yellow,annual\n")

# Read the file contents and format the information about each row
def contents_of_file(filename):
  return_string = ""

  # Call the function to create the file 
  create_file(filename)

  # Open the file
  with open(filename) as file:
    # Read the rows of the file into a dictionary
    rows = csv.reader(file)
    # Process each row
    for row in rows:
      color,name,role = row
      # Format the return string for data rows only

      return_string += "a {} {} is {}\n".format(color,name,role)
  return return_string

#Call the function
print(contents_of_file("flowers.csv"))
```

Question 3
#Practice Quiz: Advanced Regular Expressions
 We're working with a CSV file, which contains employee information. Each record has a name field, followed by a phone number field, and a role field. The phone number field contains U.S. phone numbers, and needs to be modified to the international format, with "+1-" in front of the phone number. Fill in the regular expression, using groups, to use the transform_record function to do that.


``` python
import re
def transform_record(record):
  new_record = re.sub(r",(\d{3})",r",+1-\1",record)
  return new_record

print(transform_record("Sabrina Green,802-867-5309,System Administrator")) 
# Sabrina Green,+1-802-867-5309,System Administrator

print(transform_record("Eli Jones,684-3481127,IT specialist")) 
# Eli Jones,+1-684-3481127,IT specialist

print(transform_record("Melody Daniels,846-687-7436,Programmer")) 
# Melody Daniels,+1-846-687-7436,Programmer

print(transform_record("Charlie Rivera,698-746-3357,Web Developer")) 
# Charlie Rivera,+1-698-746-3357,Web Developer

```

Question 2
#Reading & Writing CSV Files
 Using the CSV file of flowers again, fill in the gaps of the contents_of_file function to process the data without turning it into a dictionary. How do you skip over the header record with the field names?

``` python
import os
import csv

# Create a file with data in it
def create_file(filename):
  with open(filename, "w") as file:
    file.write("name,color,type\n")
    file.write("carnation,pink,annual\n")
    file.write("daffodil,yellow,perennial\n")
    file.write("iris,blue,perennial\n")
    file.write("poinsettia,red,perennial\n")
    file.write("sunflower,yellow,annual\n")

# Read the file contents and format the information about each row
def contents_of_file(filename):
  return_string = ""

  # Call the function to create the file 
  create_file(filename)

  # Open the file
  with open(filename) as file:
    # Read the rows of the file into a dictionary
    rows = csv.reader(file)
    # Process each row
    for row in rows:
      color,name,role = row
      # Format the return string for data rows only

      return_string += "a {} {} is {}\n".format(color,name,role)
  return return_string

#Call the function
print(contents_of_file("flowers.csv"))
```

The multi_vowel_words function returns all words with 3 or more consecutive vowels (a, e, i, o, u). Fill in the regular expression to do that.

``` python
import re
def multi_vowel_words(text):
  pattern = r"(\w+[a,e,i,o,u]{3,}\w+)"
  result = re.findall(pattern, text)
  return result

print(multi_vowel_words("Life is beautiful")) 
# ['beautiful']

print(multi_vowel_words("Obviously, the queen is courageous and gracious.")) 
# ['Obviously', 'queen', 'courageous', 'gracious']

print(multi_vowel_words("The rambunctious children had to sit quietly and await their delicious dinner.")) 
# ['rambunctious', 'quietly', 'delicious']

print(multi_vowel_words("The order of a data queue is First In First Out (FIFO)")) 
# ['queue']

print(multi_vowel_words("Hello world!")) 
# []

```
Question 3

The transform_comments function converts comments in a Python script into those usable by a C compiler. This means looking for text that begins with a hash mark (#) and replacing it with double slashes (//), which is the C single-line comment indicator. For the purpose of this exercise, we'll ignore the possibility of a hash mark embedded inside of a Python command, and assume that it's only used to indicate a comment. We also want to treat repetitive hash marks (##), (###), etc., as a single comment indicator, to be replaced with just (//) and not (#//) or (//#). Fill in the parameters of the substitution method to complete this function: 
``` python
import re
def transform_comments(line_of_code):
  result = re.sub(r"[\#]{1,}", "//",line_of_code)
  return result

print(transform_comments("### Start of program")) 
# Should be "// Start of program"
print(transform_comments("  number = 0   ## Initialize the variable")) 
# Should be "  number = 0   // Initialize the variable"
print(transform_comments("  number += 1   # Increment the variable")) 
# Should be "  number += 1   // Increment the variable"
print(transform_comments("  return(number)")) 
# Should be "  return(number)"
```
