# web-scrappe1
Python Web Scraping Tutorial: Step-By-Step
Oxylabs promo code

Table of Contents
Web Scraping in 5 Lines of Code
Components of a Web Scraping with Python Code
Python Libraries
Python Web Scraping: Working with Requests
BeautifulSoup
Find Methods in BeautifulSoup4
Finding Multiple Elements
Finding Nested Elements
Exporting the data
Other Tools
In this Python Web Scraping Tutorial, we will outline everything needed to get started with web scraping. We will begin with simple examples and move on to relatively more complex.

Python is arguably the most suitable programming language for web scraping because of its ease and a plethora of open source libraries. Some libraries make it easy to extract the data and to transform the data into any format needed, be it a simple CSV, to a more programmer-friendly JSON, or even save directly to the database.

Web scraping with Python is so easy that it can be done in as little as 5 lines of code.

Web Scraping in 5 Lines of Code
Write these five lines in any text editor, save as a .py file, and run with Python. Note that this code assumes that you have the libraries installed. More on this later.

import requests
from bs4 import BeautifulSoup
response = requests.get("https://en.wikipedia.org/wiki/Web_scraping")
bs = BeautifulSoup(response.text,"lxml")
print(bs.find("p").text)
This will go to the Wikipedia page for the web scraping and print the first paragraph on the terminal. This code shows the simplicity and power of Python. You will find this code in webscraping_5lines.py file.

Components of a Web Scraping with Python Code
The main building blocks for any web scraping code is like this:

Get HTML
Parse HTML into Python object
Save the data extracted
In most cases, there is no need to use a browser to get the HTML. While HTML contains the data, the other files that the browser loads, like images, CSS, JavaScript, etc., just make the website pretty and functional. Web scraping is focused on data. Thus in most cases, there is no need to get these helper files.

There will be some cases when you do need to open the browser. Python makes that easy too.

Python Libraries
Web scraping with Python is easy due to the many useful libraries available

A barebones installation of Python isn’t enough for web scraping. One of the Python advantages is a large selection of libraries for web scraping. For this Python web scraping tutorial, we’ll be using three important libraries – requests, BeautifulSoup, and CSV.

The Requests library is used to get the HTML files, bypassing the need to use a browser
BeautifulSoup is used to convert the raw HTML into a Python object, also called parsing. We will be working with Version 4 of this library, also know as bs4 or BeautifulSoup4.
The CSV library is part of the standard Python installation. No separate installation is required.
Typically, a virtual environment is used to install these libraries. If you don't know about virtual environments, you can install these libraries in the user folder.
To install these libraries, start the terminal or command prompt of your OS and type in:

pip install requests BeautifulSoup4 lxml
Depending on your OS and settings, you may need to use pip3 instead of pip. You may also need to use --user switch, depending on your settings.

Python Web Scraping: Working with Requests
The requests library eliminates the need to launch a browser, which will load the web page and all the supporting files that make the website pretty. The data that we need to extract is in the HTML. Requests library allows us to send a request to a webpage and get the response HTML.

Open a text editor of your choice, Visual Studio Code, PyCharm, Sublime Text, Jupyter Notebooks, or even notepad. Use the one which you are familiar with.

Type in these three lines:

import requests
 
url_to_parse = "https://en.wikipedia.org/wiki/Python_(programming_language)"
response = requests.get(url_to_parse)
print(response)
Save this file as a python file with .py extension and run it from your terminal. The output should be something like this:

<Response (200)>
It means that the response has been received and the status code is 200. The HTTP Response code 200 means a successful response. Response codes in the range of 400 and 500 mean error. You can read more about the response codes here.

To get the HTML from the response object, we can simply use the .text attribute.

print(response.text)
This will print the HTML on the terminal. The first few characters will be something like this:

<!DOCTYPE html>\n<html class="client-nojs" lang=" ...
If we check the data type of this, it will be a string. The next step is to convert this string into something that can be queried to find the specific information.

Meet BeautifulSoup!

BeautifulSoup
Beautiful Soup provides simple methods for navigating, searching, and modifying the HTML. It takes care of encoding by automatically converting into UTF-8. Beautiful Soup sits on top of popular Python parsers like lxml and html5lib. It is possible to use lxml directly to query documents, but BeautifulSoup allows you to try out different parsing strategies without changing the code.

The first step is to decide the parser that you want to use. Usually, lxml is the most commonly used. This will need a separate install.

pip install lxml
Once beautifulsoup4 and lxml is installed, we can create an object of BeautifulSoup:

soup = BeautifulSoup(response_text, 'lxml')
Now we have access to several methods to query the HTML elements. For example, to get the title of the page, all we need to do is access the tag name like an attribute:

print(soup.title)
# OUTPUT: 
# <title>Python (programming language) - Wikipedia</title>

print(soup.title.text)
# OUTPUT:
# Python (programming language) - Wikipedia
Note that to get the text inside the element, we simply used the text attribute.

Similarly soup.h1 will return the first h1 tag it finds:

print(soup.h1)

# OUTPUT:
# <h1 class="firstHeading" id="firstHeading">Python (programming language)</h1>
Find Methods in BeautifulSoup4
