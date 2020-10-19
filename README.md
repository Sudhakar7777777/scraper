# scraper

Repo to show some ways to do Web Scraping.

1. Scrapy (Python)
2. BeautifulSoup (Python)
3. Colly (Golang)

# Scrapy Notes

### Create a new scrapy project

```
scrapy startproject tutorial
cd tutorial
```

### Create a custom spider

```
touch spiders/quotes_spider.py
```

And add the spider class logic...

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

more css and xpath selector options..

```
response.css('title')
response.css('title').get()
response.css('title::text').get()

response.css('h3::text').get()
response.css('h3::text')[1].get()
response.css('h3::text').getall()

response.css('.post-header').get()
response.css('.post-header a').get()

response.css('p::text').re(r'scraping')
response.css('p::text').re(r's\w+')
response.css('p::text').re(r'(\w+) you (\w+)')

response.xpath('//h3')
response.xpath('//h3/text()').extract()
response.xpath('//*[@id="hs_cos_wrapper_module_1523032069834331"]/div/div/div/div/div[1]/div[2]/div[2]/div/span[2]/a/text()').getall()
```

### Running the spider and overwrite output to json file

Note: quotes is the spider name you have defined in file: spiders/quotes_spider.py

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
