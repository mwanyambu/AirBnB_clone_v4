# AirBnB Clone - The Console
The console is the first segment of the AirBnB project at Holberton School that will collectively cover fundamental concepts of higher level programming. The goal of AirBnB project is to eventually deploy our server a simple copy of the AirBnB Website(HBnB). A command interpreter is created in this segment to manage objects for the AirBnB(HBnB) website.

#### Functionalities of this command interpreter:
* Create a new object (ex: a new User or a new Place)
* Retrieve an object from a file, a database etc...
* Do operations on objects (count, compute stats, etc...)
* Update attributes of an object
* Destroy an object

## Table of Content
* [Environment](#environment)
* [Installation](#installation)
* [File Descriptions](#file-descriptions)
* [Usage](#usage)
* [Examples of use](#examples-of-use)
* [Bugs](#bugs)
* [Authors](#authors)
* [License](#license)

## Environment
This project is interpreted/tested on Ubuntu 14.04 LTS using python3 (version 3.4.3)

## Installation
* Clone this repository: `git clone "https://github.com/alexaorrico/AirBnB_clone.git"`
* Access AirBnb directory: `cd AirBnB_clone`
* Run hbnb(interactively): `./console` and enter command
* Run hbnb(non-interactively): `echo "<command>" | ./console.py`

## File Descriptions
[console.py](console.py) - the console contains the entry point of the command interpreter. 
List of commands this console current supports:
* `EOF` - exits console 
* `quit` - exits console
* `<emptyline>` - overwrites default emptyline method and does nothing
* `create` - Creates a new instance of`BaseModel`, saves it (to the JSON file) and prints the id
* `destroy` - Deletes an instance based on the class name and id (save the change into the JSON file). 
* `show` - Prints the string representation of an instance based on the class name and id.
* `all` - Prints all string representation of all instances based or not on the class name. 
* `update` - Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file). 

#### `models/` directory contains classes used for this project:
[base_model.py](/models/base_model.py) - The BaseModel class from which future classes will be derived
* `def __init__(self, *args, **kwargs)` - Initialization of the base model
* `def __str__(self)` - String representation of the BaseModel class
* `def save(self)` - Updates the attribute `updated_at` with the current datetime
* `def to_dict(self)` - returns a dictionary containing all keys/values of the instance

Classes inherited from Base Model:
* [amenity.py](/models/amenity.py)
* [city.py](/models/city.py)
* [place.py](/models/place.py)
* [review.py](/models/review.py)
* [state.py](/models/state.py)
* [user.py](/models/user.py)

#### `/models/engine` directory contains File Storage class that handles JASON serialization and deserialization :
[file_storage.py](/models/engine/file_storage.py) - serializes instances to a JSON file & deserializes back to instances
* `def all(self)` - returns the dictionary __objects
* `def new(self, obj)` - sets in __objects the obj with key <obj class name>.id
* `def save(self)` - serializes __objects to the JSON file (path: __file_path)
* ` def reload(self)` -  deserializes the JSON file to __objects

#### `/tests` directory contains all unit test cases for this project:
[/test_models/test_base_model.py](/tests/test_models/test_base_model.py) - Contains the TestBaseModel and TestBaseModelDocs classes
TestBaseModelDocs class:
* `def setUpClass(cls)`- Set up for the doc tests
* `def test_pep8_conformance_base_model(self)` - Test that models/base_model.py conforms to PEP8
* `def test_pep8_conformance_test_base_model(self)` - Test that tests/test_models/test_base_model.py conforms to PEP8
* `def test_bm_module_docstring(self)` - Test for the base_model.py module docstring
* `def test_bm_class_docstring(self)` - Test for the BaseModel class docstring
* `def test_bm_func_docstrings(self)` - Test for the presence of docstrings in BaseModel methods

TestBaseModel class:
* `def test_is_base_model(self)` - Test that the instatiation of a BaseModel works
* `def test_created_at_instantiation(self)` - Test created_at is a pub. instance attribute of type datetime
* `def test_updated_at_instantiation(self)` - Test updated_at is a pub. instance attribute of type datetime
* `def test_diff_datetime_objs(self)` - Test that two BaseModel instances have different datetime objects

[/test_models/test_amenity.py](/tests/test_models/test_amenity.py) - Contains the TestAmenityDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_amenity(self)` - Test that models/amenity.py conforms to PEP8
* `def test_pep8_conformance_test_amenity(self)` - Test that tests/test_models/test_amenity.py conforms to PEP8
* `def test_amenity_module_docstring(self)` - Test for the amenity.py module docstring
* `def test_amenity_class_docstring(self)` - Test for the Amenity class docstring

[/test_models/test_city.py](/tests/test_models/test_city.py) - Contains the TestCityDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_city(self)` - Test that models/city.py conforms to PEP8
* `def test_pep8_conformance_test_city(self)` - Test that tests/test_models/test_city.py conforms to PEP8
* `def test_city_module_docstring(self)` - Test for the city.py module docstring
* `def test_city_class_docstring(self)` - Test for the City class docstring

[/test_models/test_file_storage.py](/tests/test_models/test_file_storage.py) - Contains the TestFileStorageDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_file_storage(self)` - Test that models/file_storage.py conforms to PEP8
* `def test_pep8_conformance_test_file_storage(self)` - Test that tests/test_models/test_file_storage.py conforms to PEP8
* `def test_file_storage_module_docstring(self)` - Test for the file_storage.py module docstring
* `def test_file_storage_class_docstring(self)` - Test for the FileStorage class docstring

[/test_models/test_place.py](/tests/test_models/test_place.py) - Contains the TestPlaceDoc class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_place(self)` - Test that models/place.py conforms to PEP8.
* `def test_pep8_conformance_test_place(self)` - Test that tests/test_models/test_place.py conforms to PEP8.
* `def test_place_module_docstring(self)` - Test for the place.py module docstring
* `def test_place_class_docstring(self)` - Test for the Place class docstring

[/test_models/test_review.py](/tests/test_models/test_review.py) - Contains the TestReviewDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_review(self)` - Test that models/review.py conforms to PEP8
* `def test_pep8_conformance_test_review(self)` - Test that tests/test_models/test_review.py conforms to PEP8
* `def test_review_module_docstring(self)` - Test for the review.py module docstring
* `def test_review_class_docstring(self)` - Test for the Review class docstring

[/test_models/state.py](/tests/test_models/test_state.py) - Contains the TestStateDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_state(self)` - Test that models/state.py conforms to PEP8
* `def test_pep8_conformance_test_state(self)` - Test that tests/test_models/test_state.py conforms to PEP8
* `def test_state_module_docstring(self)` - Test for the state.py module docstring
* `def test_state_class_docstring(self)` - Test for the State class docstring

[/test_models/user.py](/tests/test_models/test_user.py) - Contains the TestUserDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_user(self)` - Test that models/user.py conforms to PEP8
* `def test_pep8_conformance_test_user(self)` - Test that tests/test_models/test_user.py conforms to PEP8
* `def test_user_module_docstring(self)` - Test for the user.py module docstring
* `def test_user_class_docstring(self)` - Test for the User class docstring


## Examples of use
```
vagrantAirBnB_clone$./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  all  create  destroy  help  quit  show  update

(hbnb) all MyModel
** class doesn't exist **
(hbnb) create BaseModel
7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) all BaseModel
[[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}]
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}
(hbnb) destroy BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
** no instance found **
(hbnb) quit
```

## Bugs
No known bugs at this time. 

## Authors
John Mwanyasi - [Github] (https://github.com/mwanyambu) <jmwanyambu@gmail.com>
Caleb Kegera - <kegesheddy@gmail.com>
Alexa Orrico - [Github](https://github.com/alexaorrico) / [Twitter](https://twitter.com/alexa_orrico)  
Jennifer Huang - [Github](https://github.com/jhuang10123) / [Twitter](https://twitter.com/earthtojhuang)  
Jhoan Zamora - [Github](https://github.com/jzamora5) / [Twitter](https://twitter.com/JhoanZamora10)  
David Ovalle - [Github](https://github.com/Nukemenonai) / [Twitter](https://twitter.com/disartDave)

Second part of Airbnb: Joann Vuong
## License
Public Domain. No copy write protection. 

##Air_BnB_clone_v4
Based on web_flask, copy: web_flask/static, web_flask/templates/100-hbnb.html, web_flask/__init__.py and web_flask/100-hbnb.py into the web_dynamic folder
Rename 100-hbnb.py to 0-hbnb.py
Rename 100-hbnb.html to 0-hbnb.html
Update 0-hbnb.py to replace the existing route to /0-hbnb/

Replace the route 0-hbnb with 1-hbnb in the file 1-hbnb.py (based on 0-hbnb.py)

Create a new template 1-hbnb.html (based on 0-hbnb.html) and update it:

Import JQuery in the <head> tag
Import the JavaScript static/scripts/1-hbnb.js in the <head> tag
In 1-hbnb.html and the following HTML files, add this variable cache_id as query string to the above <script> tag
Add a <input type="checkbox"> tag to the li tag of each amenity
The new checkbox must be at 10px on the left of the Amenity name
Add to the input tags of each amenity (<li> tag) the attribute data-id=":amenity_id" => this will allow us to retrieve the Amenity ID from the DOM
Add to the input tags of each amenity (<li> tag) the attribute data-name=":amenity_name" => this will allow us to retrieve the Amenity name from the DOM
Write a JavaScript script (static/scripts/1-hbnb.js):

Your script must be executed only when DOM is loaded
You must use JQuery
Listen for changes on each input checkbox tag:
if the checkbox is checked, you must store the Amenity ID in a variable (dictionary or list)
if the checkbox is unchecked, you must remove the Amenity ID from the variable
update the h4 tag inside the div Amenities with the list of Amenities checked

Update the API entry point (api/v1/app.py) by replacing the current CORS CORS(app, origins="0.0.0.0") by CORS(app, resources={r"/api/v1/*": {"origins": "*"}}).

Change the route 1-hbnb to 2-hbnb in the file 2-hbnb.py (based on 1-hbnb.py)

Create a new template 2-hbnb.html (based on 1-hbnb.html) and update it:

Import the JavaScript static/scripts/2-hbnb.js in the <head> tag (instead of 1-hbnb.js)
Add a new div element in the header tag:
Attribute ID should be api_status
Align to the right
Circle of 40px diameter
Center vertically
At 30px of the right border
Background color #cccccc
Also add a class available for this new element in web_dynamic/static/styles/3-header.css:
Background color #ff545f
Write a JavaScript script (static/scripts/2-hbnb.js):

Based on 1-hbnb.js
Request http://0.0.0.0:5001/api/v1/status/:
If in the status is “OK”, add the class available to the div#api_status
Otherwise, remove the class available to the div#api_status
To start the API in the port 5001:

Replace the route 2-hbnb with 3-hbnb in the file 3-hbnb.py (based on 2-hbnb.py)

Create a new template 3-hbnb.html (based on 2-hbnb.html) and update it:

Import the JavaScript static/scripts/3-hbnb.js in the <head> tag (instead of 2-hbnb.js)
Remove the entire Jinja section of displaying all places (all article tags)
Write a JavaScript script (static/scripts/3-hbnb.js):

Based on 2-hbnb.js
Request http://0.0.0.0:5001/api/v1/places_search/:
Description of this endpoint here. If this endpoint is not available, you will have to add it to the API (you can work all together for creating this endpoint)
Send a POST request with Content-Type: application/json and an empty dictionary in the body - cURL version: curl "http://0.0.0.0:5001/api/v1/places_search" -XPOST -H "Content-Type: application/json" -d '{}'
Loop into the result of the request and create an article tag representing a Place in the section.places. (you can remove the Owner tag in the place description)
The final result must be the same as previously, but now, places are loaded from the front-end, not from the back-end!

Replace the route 3-hbnb with 4-hbnb in the file 4-hbnb.py (based on 3-hbnb.py)

Create a new template 4-hbnb.html (based on 3-hbnb.html) and update it:

Import the JavaScript static/scripts/4-hbnb.js in the <head> tag (instead of 3-hbnb.js)
Write a JavaScript script (static/scripts/4-hbnb.js):

Based on 3-hbnb.js
When the button tag is clicked, a new POST request to places_search should be made with the list of Amenities checked
Now you have the first filter implemented, enjoy!
