# facebook-scrap-selenium


## Installation
- open terminal and type the following command: "git clone https://github.com/HassenFenni/facebook-scrap-selenium-helfenni/"
- cd into the project and execute the following command: "pip install -r requirements.txt" 
- add your facebook credentials in the text file
- add your own mongoDB client in order to insert results into the DB (last code snippets in 'src') 



## How it works ? 

Methodology:
1) pages_to_scrape = ["France 24", ...]
2) search in the page of france 24 (or other news page) for 
keyword = "jacques chirac décès" 
3) scroll + get all post url's 
4) go through urls one by one and scrap the first post for each URL 
(using "https://mbasic.facebook.com/..." can make it easier)
5) format results as JSON
6) insert JSON into MongoDB 

#### inputs: 
1) fb credentials (e-mail + pwd)
2) pages_to_scrape // list of page names to scrap // ex: ['page_name1','page_name2',...]
3) n_posts // int #number of posts to scrape from search results // range: 0-number of publications 
4) LIMIT_COMMENTS // int // range: 0-number of comments  
5) keyword // string // ex: "jacques chirac décès"

#### output:
- dictionary containing facebook posts data regarding a particular subject : \n
{publication author, title, photo, publication date, comments = {'author':'author', 'comment': 'comment', 'date': 'date, 'replies': '...'}}
- inserting into mongoDB

#### limits: 
1) Due to the time cost I limited the number of comments per post to 30 
& posts to scrape per page to 25
2) scraping only lvl0 comments

#### Possible additions: 
1) Détecter les mots clés dans la phrase (ex: "le décès du président Jacques Chirac")
solutions : Graph-based approaches , Conditional Random Fields (CRF), SVM’s, TF-IDF, …
2) Générer une liste de synonymes pour les mots clés qui ne sont pas des noms/prénoms
-solutions for extracting names : Named Entity Recognition (NER) 
-solutions for synonym extraction : word2vec (skip-gram), …
3) Effectuer plusieurs recherches selon les mots clés + les synonymes
