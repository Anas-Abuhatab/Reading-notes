# Web Scraping

### Web Scrape with Python in 4 minutes
- Web scraping is a technique to automatically access and extract large amounts of information from a website.
- Most sites prohibit you from using the data for commercial purposes.
- Make sure you are not downloading data at too rapid a rate because this may break the website.
- Inspect to see the raw code on a webpage. 
- Start by importing the following libraries:
```
import requests
import urllib.request
import time
from bs4 import BeautifulSoup
```
- set the url to the website and access the site with our requests library:
```
url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
``` 
- If access was successful, then it will output <Response [200]> or something. 
- parse the html with BeautifulSoup so that we can work with a nicer, nested BeautifulSoup data structure:
```
soup = BeautifulSoup(response.text, “html.parser”)
```
- use the method .findAll to locate all of our <a> tags:
```
soup.findAll('a')
```
- extract the actual link that we want. Let’s test out the first link.
```
one_a_tag = soup.findAll(‘a’)[38]
link = one_a_tag[‘href’]
```
- Finished code:
```
  # Import libraries
import requests
import urllib.request
import time
from bs4 import BeautifulSoup

# Set the URL you want to webscrape from
url = 'http://web.mta.info/developers/turnstile.html'

# Connect to the URL
response = requests.get(url)

# Parse HTML and save to BeautifulSoup object¶
soup = BeautifulSoup(response.text, "html.parser")

# To download the whole data set, let's do a for loop through all a tags
line_count = 1 #variable to track what line you are on
for one_a_tag in soup.findAll('a'):  #'a' tags are for links
    if line_count >= 38: #code for text files starts at line 36
        link = one_a_tag['href']
        download_url = 'http://web.mta.info/developers/'+ link
        urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:]) 
        time.sleep(1) #pause the code for a sec
    #add 1 for next line
    line_count +=1
```
