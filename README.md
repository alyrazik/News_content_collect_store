# News_content_collect_store
This repo contains code to crawl for articles from the BBC, cleanse them, store them in MongoDB, and then make it available to search via an API

The file contains the API code and some code applying it.

Several functions provides some abstraction and allows for re-use.

1. give_links(url, parent): 
Takes a url, and its parent address and returns a list of absolute addresses of web links orginitating from it.

2. is_news_article(link):  
Takes a web link address and tests whether the link contains a news article in BBC. Returns 1 if True, 0 otherwise.  

3. follow_links(origin_link, test_func, n_other_links_to_follow = 1): 
Takes a link and starts following all links it contained searching for a pattern specificed by boolean function test_func. It adds them to matching_urls list. Other links that doesn't match the specified pattern are added to another list (other_urls). The function will then crawl a number of them specified by another function parameter.

4. retrieve_documents(database, collection): 
Takes a MongoDB database and collection name, and returns all documents in collection to a pandas dataframe. You have to have an established connection. 

5. search(search_text, database, collection): 
Takes a a string containing keywords and outputs all relevant articles to any of them.

I have created a hosted MongodDB atlas database and connected to it in the code using my credentials (provided in the code)



