# facebook-scrap-selenium


## Installation
- open terminal and type the following command: "git clone https://github.com/HassenFenni/facebook-scrap-selenium-helfenni/"
- cd into the project and execute the following command: "pip install -r requirements.txt" 
- add your facebook credentials in the text file
- add your own mongoDB client in order to insert results into the DB (last code snippets in 'src')
/!\ you must set your FB language preference to French 




## How it works ? 

#### Methodology:
1) pages_to_scrape = ["France 24", "lemonde.fr", "franceinfo", ...] #change to your needs
2) keyword = "jacques chirac décès" #change to your needs
3) search in the page of france 24 (or other news page) for keyword
3) scroll + get all post url's 
4) go through urls one by one and scrap the first post for each URL 
(using "https://mbasic.facebook.com/...")
5) format results as JSON
6) insert JSON into MongoDB 

#### inputs: 
1) fb credentials (e-mail + pwd)
2) "pages_to_scrape": list of page names to scrap ; ex: ['page_name1','page_name2',...]
3) "n_posts_limit": int for the #number of posts to scrape from search results ; range: 0-number of publications for that particular search == (len(urls_to_scrape))
4) "LIMIT_COMMENTS": int for the #number of comments to scrape per post ; range: 0-number of comments  
5) "keyword": string ; ex: "jacques chirac décès"

#### output:
- dictionary containing facebook posts data regarding a particular subject : <br/>
{publication author, title, photo, publication date, comments = {'author':'author', 'comment': 'comment', 'date': 'date, 'replies': '...'}}
- inserting into mongoDB

#### limits: 
- scraping only the comments (no replies)
