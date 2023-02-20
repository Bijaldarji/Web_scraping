# Web_scraping
I developed this project to scrap data from website 

from bs4 import BeautifulSoup 

import requests 

import csv

import pandas as pd

Product=[]
Price = []
Description = []
Reviews = []



url="https://www.flipkart.com/search?q=mobiles+under+50000&otracker=search&otracker1=search&marketplace=FLIPKART&as-show=on&as=off&page=1"
r = requests.get(url)
print(r)    


soup = BeautifulSoup(r.text,'lxml')
print(soup)
box = soup.find("div",class_="_1YokD2 _3Mn1Gg") 
names = box.find_all("div",class_="_4rR01T")
print(names)

for i in names:
  name = i.text
  Product_name.append(name)
print(Product_name)



price = box.find_all("div",class_="_30jeq3 _1_WHN1")

for i in price:
  name = i.text
  Price.append(name)
print(Price)



desc = box.find_all("ul",class_="_1xgFaf")
for i in desc:
  name = i.text
  Description.append(name)
print(Description)



reviews = box.find_all("div",class_="_3LWZlK")

for i in reviews:
  name = i.text
  Reviews.append(name)
print(Reviews)
df = pd.DataFrame({"Product_name":Product_name,"Price":Price,"Description":Description,"Reviews":Reviews})
print(df)


