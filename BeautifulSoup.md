from bs4 import BeautifulSoup
import requests

response = requests.get("https://news.ycombinator.com/news")
yc_web_page = response.text

soup = BeautifulSoup(yc_web_page, "html.parser")

article_tag = soup.find('span', class_='titleline')
article_text = article_tag.getText()
article_link = soup.find('span', class_='titleline').find('a').get('href')
article_upvote = soup.find('span', class_='score').getText()

print(article_text)
print(article_link)
print(article_upvote)

