__Matthew Lee__

__Python & Django Notes/Documentation
Python__

.format()

subject = "Treehouse loves {}".format(name)

Slicing

  def first_4(iter):
    return iter[:4]
  def first_and_last_4(iter):
    return iter[:4] + iter[-4:]
  def odds(iter):
    return iter[1::2]

Dictionaries

*args and **kwargs
Allow us to pass in a variable number of arguments to a function.
*args is for non-keyword variable
def test_var_args(f_arg, *argv):
    print "first normal arg:", f_arg
    for arg in argv:
        print "another arg through *argv :", arg
test_var_args('yasoob','python','eggs','test')
first normal arg: yasoob
another arg through *argv : python
another arg through *argv : eggs
another arg through *argv : test


**kwargs
kwargs allow us to pass keyworded vairable length of arguments to
a function. Use it when you want to handle named arguments in a function.

def greet_me(**kwargs):
    if kwargs is not None:
        for key, value in kwargs.iteritems():
            print "%s == %s" %(key,value)

>>> greet_me(name="yasoob")
name == yasoob


Packing and Unpacking Arguments
**
**{“key1” = 1, “key2”= 2} -> this will just send the keyword arguments to a function etc.

Def packer(**kwargs):
	print(kwargs)
Packer = (name=”kenneth”, num=42, spanish_inquisition =None)

Def unpacker(first_name=None, last_name=None):
	If first_name and last_name:
		print(“Hi {} {}”.format(first_name,last_name))
	Else:
		print(“Hi noname”)


Tuples
A = (1,2,3)

Packing Tuples
ex)
def multiply(*args):
    product = 1
    for num in args:
        product *= num
    return product


Enumerate() -> takes an ordered iterable like a list, string, or tuple, walks through,

Returning multiple variables tuple.
e.g) string = “matt is a StudenT.”
return string.lower(), string.upper(), string.title(), string[::-1]
































Object-Oriented Python

Class
__init__
class Customer(object):

    """A customer of ABC Bank with a checking account. Customers have the
    following properties:

    Attributes:
        name: A string representing the customer's name.
        balance: A float tracking the current balance of the customer's account.
    """

    def __init__(self, name, balance=0.0):
        """Return a Customer object whose name is *name* and starting
        balance is *balance*."""
        self.name = name
        self.balance = balance

    def withdraw(self, amount):
        """Return the balance remaining after withdrawing *amount*
        dollars."""
        if amount > self.balance:
            raise RuntimeError('Amount greater than available balance.')
        self.balance -= amount
        return self.balance

    def deposit(self, amount):
        """Return the balance remaining after depositing *amount*
        dollars."""
        self.balance += amount
        return self.balance

Subclass

If there is a monster class we built, we can create a subclass called zombies.

eg)
From Monster import monster
Class zombies(monster):




setattr()
- can be used when the name of the attribute you wish to set is
contained in a variable.
- For example, setattr(x, 'foobar', 123) is equivalent to x.foobar = 123.

getattr()
- getattr(object, name[, default]) Returns the value of the named attribute of
object. name must be a string. If the string is the name of one of the
object’s attributes, the result is the value of that attribute.
- For example, getattr(x, 'foobar') is equivalent to x.foobar.


__str__



__DJANGO:__

- to start a project
django-admin startproject [projectname]

- to run server
python manage.py runserver

Migrations
- are a way of moving a database from one design,
a specific set of tables and columns, to a new one.
- reversible

db.sqlite3
- the default database in django

HttpReponse
- is the class that represents an HTTP response back to the client.

Django uses Regular Expressions for urls.

urls.py

- from django.conf.urls import url
- from django.contrib import admin

- add
from . import views

urlpatterns = [
    url(r'^admin/', admin.site.urls),
]

url()
- is a function that constructs a special object
that Django uses to join URLs to view functions.

plugins

Building my first app

- Django projects contain multiple Django apps. Each app generally encompasses a specific area of functionality.

$python manage.py startapp
- creates the skeleton of an app  including the views, models, and tests files.


ORM (Object Relational Mapper)
- classes (models)

django.db.models
- has most of the model functionality you'll use to create models and their fields.

- DateTimeField holds datetime objects.

- CharField holds strings.
TextField holds an unspecified amount of text.

$ python manage.py makemigrations [app]
  -  will make the migrations for a specific app.

python manage.py migrate [app]

- will run the pending migrations for a specific app. If you leave off the app name, any pending migrations for any apps will be run.
