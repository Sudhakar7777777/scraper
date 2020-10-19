# scraper

Repo to show some ways to do Web Scraping.

1. Scrapy (Python)
2. BeautifulSoup (Python)
3. Colly (Golang)

# Scrapy Notes

### Running the scrapy shell

Learn about parsing page contents in an interactive shell

```
scrapy shell 'http://quotes.toscrape.com/page/1/'

>>> response.css('title').getall()

>>> response.css('title::text').getall()

>>> response.css('title::text').re(r'(\w+) to (\w+)')

>>> response.xpath('//title/text()').get()

>>> response.css("div.quote")

>>> for quote in response.css("div.quote"):
...     text = quote.css("span.text::text").get()
...     author = quote.css("small.author::text").get()
...     tags = quote.css("div.tags a.tag::text").getall()
...     print(dict(text=text, author=author, tags=tags))
```

### Running the spider and overwrite output to json file

```
scrapy crawl quotes -O quotes.json
```

### Running the spider and append output to existing .jl (json line) file

```
scrapy crawl quotes -o quotes.jl
```

```
scrapy crawl authors -o authors.jl
```

# Reference

- Learning Web Scraping:

  - [Scrapy Docs](https://docs.scrapy.org/en/latest/index.html)
  - [BeautifulSoup Docs](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
  - [Colly Docs](http://go-colly.org/docs/)

- Learning Python:
  - [Python Docs](https://docs.python.org/3/tutorial/)
  - [Automate the Boring Stuff With Python](https://automatetheboringstuff.com/)
  - [How To Think Like a Computer Scientist](http://openbookproject.net/thinkcs/python/english3e/)
  - [Learn Python 3 The Hard Way](https://learnpythonthehardway.org/python3/)
