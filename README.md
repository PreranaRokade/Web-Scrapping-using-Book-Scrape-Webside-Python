# Web-Scrapping-using-Book-Scrape-Webside-Python
pip install requests beautifulsoup4
import requests
from bs4 import BeautifulSoup
import csv
url = 'http://books.toscrape.com/'
def scrape_books(url):
    # Send a request to the website
    response = requests.get(url)
    
    
    
def scrape_books(url):
import requests
from bs4 import BeautifulSoup
import csv

# Define the URL of the website to scrape
url = 'http://books.toscrape.com/'

# Function to scrape the webpage
def scrape_books(url):
    # Send a request to the website
    response = requests.get(url)

    # Check if the request was successful
    if response.status_code == 200:
        # Parse the HTML content using BeautifulSoup
        soup = BeautifulSoup(response.content, 'html.parser')
        
        # Find all book items
        books = soup.find_all('article', class_='product_pod')
        
        # List to store book data
        book_data = []

        # Loop through each book item and extract data
        for book in books:
            # Extract title
            title = book.h3.a['title']
            # Extract price
            price = book.find('p', class_='price_color').text
            # Append data to the list
            book_data.append([title, price])

        return book_data
    else:
        print(f"Failed to retrieve the webpage. Status code: {response.status_code}")
        return []

# Scrape the books from the first page
book_data = scrape_books(url)

# Print the scraped data
for title, price in book_data:
    print(f"Title: {title}, Price: {price}")

# Save the data to a CSV file
with open('books.csv', 'w', newline='', encoding='utf-8') as file:
    writer = csv.writer(file)
    writer.writerow(['Title', 'Price'])
    writer.writerows(book_data)

print("Data has been saved to books.csv")
