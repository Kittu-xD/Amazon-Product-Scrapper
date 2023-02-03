import requests
import re
import time
from bs4 import BeautifulSoup
import cvs

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/109.0',
    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
    'Accept-Language': 'en-US,en;q=0.5',
    # 'Accept-Encoding': 'gzip, deflate, br',
    'Connection': 'keep-alive',
    'Upgrade-Insecure-Requests': '1',
    'Sec-Fetch-Dest': 'document',
    'Sec-Fetch-Mode': 'navigate',
    'Sec-Fetch-Site': 'none',
    'Sec-Fetch-User': '?1',
}
dta = {"customer-action" : "pagination"}
base = "https://www.amazon.in/s?k=bags&crid=2M096C61O4MLT&qid=1653308124&sprefix=ba%2Caps%2C283&ref=sr_pg_1"
rsp = requests.get(base, headers=headers)
soup = BeautifulSoup(rsp.content, "html.parser")
products = soup.select('div.sg-row')
processed_names = set()
processed_prices = set()
processed_urls = set()
processed_ratings = set()
processed_reviews = set()
# print(products)
for product in products:
    # print(product)

    # Scrapping Name
    name_elements = product.select('span.a-size-medium.a-color-base.a-text-normal')
    if name_elements:
        name = name_elements[0].text
        if name not in processed_names:
            processed_names.add(name)
            with open("products.csv", "w", newline="") as f:
                writer = csv.writer(f)
                writer.writerow(["Product Name"])
                for product in processed_names:
                    writer.writerow([product])
            # print("Name :", name)

    # Scrapping Prices
    price_elements = product.select('span.a-offscreen')
    if price_elements:
        price = price_elements[0].text
        if price not in processed_prices:
            processed_prices.add(price)
            with open("products.csv", "w", newline="") as f:
                writer = csv.writer(f)
                writer.writerow(["Product Price"])
                for product in processed_prices:
                    writer.writerow([product])
            # print("Price :", price)

    # Scrapping URLs
    url_element = product.select('class.a-link-normal.s-underline-text.s-underline-link-text.s-link-style.a-text-normal')
    if url_element:
        url = url_element[0].text
        if url not in processed_urls:
            processed_urls.add(url)
            with open("products.csv", "w", newline="") as f:
                writer = csv.writer(f)
                writer.writerow(["Product URL"])
                for product in processed_urls:
                    writer.writerow([product])
            # print("Url :", url)

    # Scrapping Ratings
    rating_element = product.select('class.a-icon-alt')
    if rating_element:
        rating = rating_element[0].text
        if rating not in processed_ratings:
            processed_urls.add(rating)
            # print("Rating :", rating)
            with open("products.csv", "w", newline="") as f:
                writer = csv.writer(f)
                writer.writerow(["Rating"])
                for product in processed_ratings:
                    writer.writerow([product])

    # Scrapping Reviews 
    reviews_element = product.select('class.a-size-base.s-underline-text')
    if reviews_element:
        reviews = reviews_element[0].text
        if reviews not in processed_reviews:
            processed_urls.add(reviews)
            with open("products.csv", "w", newline="") as f:
                writer = csv.writer(f)
                writer.writerow(["Reviews"])
                for product in processed_reviews:
                    writer.writerow([product])
            # print("Reviews :", reviews)


# print(processed_names)
# print(processed_prices)
# print(processed_ratings)
# print(processed_reviews)
# print(processed_urls)




