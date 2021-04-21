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