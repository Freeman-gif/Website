# Packages


---
### Beautiful Soup:
```
pip install bs4  
pip install requests  
pip install lxml
from bs4 import BeautifulSoup  
import requests
```
```
text = """

<!DOCTYPE html>

<html>

<head>

<title>My First HTML Page</title>

</head>

<body>

<h1 class="title">Welcome to My Website!</h1>

</body>

</html>

"""
```
```
soup = BeautifulSoup(text, "lxml")

soup.find('h1', class_="title")


```



---

### Selenium

---
### Scrapy



---
#### TAGS:
#Python #library