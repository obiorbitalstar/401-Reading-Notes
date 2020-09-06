# Web Scraping
Web scraping is a technique to automatically access and extract large amounts of information from a website.

it should be fun and simple 
so here is a step by step go at it 

## 1. Inspecting the Website
The first thing that we need to do is to figure out where we can locate the links to the files we want to download inside the multiple levels of HTML tags. Simply put, there is a lot of code on a website page and we want to find the relevant pieces of code that contains our data.

* On the website, right click and click on “Inspect”. This allows you to see the raw code behind the site 
* Notice that on the top left of the console, there is an arrow symbol. ![img](https://miro.medium.com/max/30/1*OBTSehekWVX6rSXUaibd1A.png)

* If you click on this arrow and then click on an area of the site itself, the code for that particular item will be highlighted in the console

this will help you identify the location of the links to the txt files 

so now we got the links location we code 

## 2. Python Code
start by importing the following libraries 

```
import requests 
import urlib.requests 
import time 
from bs4 import BeautifulSoup   

```

then set the url for the site you want to scarp 

``` 
url = ' some url ' 
response = requests.get(url)

```
successful access reutrns <response 200 >

Next we parse the html with BeautifulSoup so that we can work with a nicer, nested BeautifulSoup data structure

```
soup = BeautifulSoup(response.text, “html.parser”)

```

We use the method .findAll to locate all of our <a> tags.

```
soup.findAll('a')

```

This code gives us every line of code that has an <a> tag

Next, let’s extract the actual link that we wan

```
one_a_tag = soup.findAll(‘a’)[38]
link = one_a_tag[‘href’]
```
This code saves the first text file to our variable link.

We can use our urllib.request library to download this file path to our computer. We provide request.urlretrieve with two parameters: file url and the filename

```
download_url = 'http://web.mta.info/developers/'+ link
urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
```

Last but not least, we should include this line of code so that we can pause our code for a second so that we are not spamming the website with requests. This helps us avoid getting flagged as a spammer.

```
time.sleep(1)

``` 