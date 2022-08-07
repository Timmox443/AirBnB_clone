# ⛱️ AirBnB Clone Project - The Console

This console is the first part of the AirBnB project at the Alx-Africa school.
This program will cover some fundamental concepts of higher level programming
that we have gone over in our curriculum. The goal of this project is to deploy
a simple clone of the AirBnB website. A command interpreter has been created
to manage objects for the website.

## 🌳 Environment:
This project has been completed on Ubuntu 20.04 using python3 (3.8.7)

## ⚙️ Installation

> Step 1 - Clone the repo locally using this command
```
gh repo clone https://github.com/Timmox443/AirBnB_clone.git
```
> Step 2 - Navigate to the folder
```
cd AirBnB_clone
```
> Step 3 - Run the console shell in interactive mode:
```
./console.py
```
> Step 4 - Type a command e.g.
```
 help
```
> Step 5 - Exit the shell
```
 quit
```

## 🚀 Operation Modes

#### Interactive mode
In the interactive mode, the console will display (alx) prompting the user to type in and execute a command. After the command is run, the prompt will appear again in a new line waiting for a new command to be entered. As long as the user doesn't quit the shell (by typing quit and pressing enter), this will go indefinitely. 
Example:

```
$ ./console.py
 help

Documented commands (type help <topic>):
========================================
EOF  help  quit

(alx)
(alx)
(alx) quit
$
```

#### Non-interactive mode

In the non-interactive mode, the console is run with a command pipped into into its execution - this way the command is run as soon as the shell starts. In this mode no prompt (alx) appears, and no further input is expected from the user.
Example:

```
$ echo "help" | ./console.py
(alx)

Documented commands (type help <topic>):
EOF  help  quit
(alx)
$
$ cat test_help
help
$
$ cat test_help | ./console.py
(alx)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(alx) 
$
```



## 🛂 Testing:
All files, classes and functions can be tested with unit tests.

**Interactive mode:** 
```
python3 -m unittest discover tests
```

**Non-interactive mode** 
```
echo "python3 -m unittest discover tests" | bash
```



## 📁 File descriptions:

### [console.py](console.py)
The console contains the entry point of the interpreter, the list of commands
the interpreter supports are as follows:
* `EOF` - exits console
* `quit` - exits console
* `create` - Creates a new instance of`BaseModel`, saves it (to the JSON file) and prints the id
* `destroy` - Deletes an instance based on the class name and id (save the change into the JSON file). 
* `show` - Prints the string representation of an instance based on the class name and id.
* `all` - Prints all string representation of all instances based or not on the class name. 
* `update` - Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file). 


### [base_model.py](/models/base_model.py)
The BaseModel class is the class which future classes will inherit from.
* `def __init__(self, *args, **kwargs)` - Initialization of the base model
* `def __str__(self)` - String representation of the BaseModel class
* `def save(self)` - Updates the attribute `updated_at` with the current datetime
* `def to_dict(self)` - returns a dictionary containing all keys/values of the instance

| FILES TO INHERIT FROM BASEMODEL  | DESCRIPTION   | ATTRIBUTES                                                                                                                           |
|----------------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [user.py](/models/user.py)       | user class    | email, password, first_name, last_name                                                                                               |
| [amenity.py](/models/amenity.py) | amenity class | name                                                                                                                                 |
| [place.py](/models/place.py)     | place class   | city_id, user_id, name, description, number_of_rooms, longitude, latitude, max_guests, number_bathrooms, price_by_night, amenity_ids |
| [review.py](/models/review.py)   | review class  | place_id, user_id, text                                                                                                              |
| [state.py](/models/state.py)     | state class   | name                                                                                                                                 |
| [city.py](/models/city.py)       | city class    | state_id, name                                                                                                                       |

### [file_storage.py](/models/engine/file_storage.py)
The file_storage file serializes instances to a JSON file & deserializes back to instances
* `def all(self)` - returns the dictionary __objects
* `def new(self, obj)` - sets in __objects the obj with key <obj class name>.id
* `def save(self)` - serializes __objects to the JSON file (path: __file_path)
* ` def reload(self)` -  deserializes the JSON file to __objects

## 🛖 Examples
```
$ ./console.py

(alx)

(alx) BaseModel.create()

a45fe3c4-3b89-4b50-91e9-213b2eae45e3

(alx) BaseModel.show(a45fe3c4-3b89-4b50-91e9-213b2eae45e3)

[BaseModel] (a45fe3c4-3b89-4b50-91e9-213b2eae45e3) {'id': 'a45fe3c4-3b89-4b50-91e9-213b2eae45e3', 'created_at': datetime.datetime(2022, 6, 29, 17, 0, 38, 333356), 'updated_at': datetime.datetime(2022, 6, 29, 17, 0, 38, 333406)}

(alx) BaseModel.destroy(a45fe3c4-3b89-4b50-91e9-213b2eae45e3)

(alx) BaseModel.show(a45fe3c4-3b89-4b50-91e9-213b2eae45e3)

** no instance found **
(alx) EOF
```
## 🐛 Bugs
No known bugs at this time.
## ✍🏽 Authors

- Timothy Mutumwa
- Etinosa Oyema
