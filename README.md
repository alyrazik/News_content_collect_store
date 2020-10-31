# News_content_collect_store
This repo contains code to crawl for articles from the BBC, cleanse them, store them in MongoDB, and then make it available to search via an API.

The purpose is to fulfill a coding challenge. Some of the used frameworks are requests, Beautifulsoup.

The file contains the API and some code applying it. Several functions provides some abstraction and allows for re-use as below:

1. give_links(url, parent): 
Takes a url, and its parent address and returns a list of absolute addresses of web links orginitating from it.

2. is_news_article(link):  
Takes a web link address and tests whether the link contains a news article in BBC. Returns 1 if True, 0 otherwise.  

3. follow_links(origin_link, test_func, n_other_links_to_follow = 1): 
Takes a link and starts following all links it contained searching for a pattern specificed by boolean function test_func. It adds them to matching_urls list. Other links that doesn't match the specified pattern are added to another list (other_urls). 

The function will then crawl a number of them specified by another function parameter (n_other_links_to_follow) which is set to 1 by default. 
Generally, increasing this number will consume more time but will yield more articles too. 

Args:
    -origin link: a string of the URL address (<string>)
    -test_func: a callable that takes a string of a URL link and outputs 1 if the link matches a specified pattern, 0 otherwise.
    -n_other_links_to_follow : number of links to follow from the other_urls list (<int>)
  Returns:
    -Two python lists containing matching_urls and other_urls

4. retrieve_documents(database, collection): 
Takes a MongoDB database and collection name, and returns all documents in collection to a pandas dataframe. You have to have an established connection. 

5. search(search_text, database, collection): 
Takes a a string containing keywords and outputs all relevant articles to any of them.

  Args:
    -search_text: a string of keywords (<string>)
    -database: MongoDB database name (<pymongo.database.Database>)
    -collection: string with the name of MongoDB collection (<string>)
  Returns:
    -A pandas dataframe containing the MongoDB contents of the returned news articles

I have created a hosted MongodDB atlas database and connected to it in the code using my credentials (provided in the code)

# Reference
Please refer to https://github.com/Isentia/Coding-Challenge who posted this coding challenge.

# Questions
Please email me at alyrazik@gmail.com
