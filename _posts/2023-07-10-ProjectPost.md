---
layout: post
title: Project
---
## Text Analysis of the Results of the Search for the Word Religion on the Website of the German Ministry of Foreign Affairs

In my project for the Digital Methods in Religious Studies course, I examined how the word "religion" is used on the official website of the Federal State of Germany. To do this, I collected information by scraping the search results page on the website and retrieving the links from those results. After that, I used software programs called Voyant Tools and AntConc to analyze the obtained results. These tools helped me study and understand the different ways the word "religion" was used on the website.

After conducting the search, I obtained a total of "315" results. However, for the initial analysis, I focused on examining only the first 20 results rather than all of them. It's important to note that the program used couldn't access documents with a .pdf extension on the web page, so I made sure that the pages I examined didn't contain any files in that format.

### Step One
In the first step, unlike the code sequence shared by Dr. Elwert under the title of text analysis, the project was created directly from the "URL" instead of the "Clipboard". This automatically generated the date, type of the article, title of the article, slug "columns" automatically.

![1](assets/image/img6.jpg)

![2](assets/image/img7.jpg)



### Step Two
The first step only gave us the results from the search page. However, since we needed the texts within the links of the news headlines, we obtained the actual links to the texts by assigning the value of the link to the website of the Federal Foreign Office of Germany to the existing slugs. **by filling 10 rows with 

grel:"https://www.auswaertiges-amt.de" + value

![3](assets/image/img8.jpg) 
### Step Three
In order to access the raw text from the code page in all links, the code views of the pages were taken with the following command:

fetching URLs based on column full_links using expression grel:value


      
### Step Four
In order to find out where the text code was hidden in the complex code page, the "Inspect" page and the "Selector" tool were used in the Firefox browser to mark the areas where the text code was hidden.
    
![4](assets/image/img9.jpg)    
    
### Step Five
Then the parseHtml code provided by Dr. Elwert was tried but without any results. Because I didn't understand exactly where I needed to change, so I asked chatgpt if my code was correct, and after a while of talking and several failed attempts to get chatgpt to provide me with the correct code, chatgpt provided me with the correct code below. 
 _I then realized that Dr. Elwert's code also worked when I added the appropriate expression, because it was the same code expression, and it was my conversation with chatgpt that helped me to put the right expression in the right spot_
            
grel:forEach(value.parseHtml().select("p.rte__paragraph"), p, p.htmlText()).join("\\n\\n")
   
![5](assets/image/img10.jpg)


   
   
### Step Six
My .csv document became a text file thanks to this code that converts all files to .txt format to make it easier to work with text.
        

![6](assets/image/img11.jpg) 
 
### Step Seven
In this step, I simply uploaded my text documents to the Voyant Tools page, and the application's own "stopper" list generated a suitable word cloud and word density lists.
        
 [project link](https://voyant-tools.org/?corpus=9f016c22ddd1ed6e308396e90ed27299&panels=cirrus,reader,trends,summary,contexts)


### Step Eight
In this step, I watched the AntConc program's user guide videos on youtube. Since it is one of the easiest tools to use and will be useful for our project, I ran the KWIC and word density tools to get the following visuals.
  
 [anticonc youtube link](https://www.youtube.com/@AntLabJPN/playlists)

![7](assets/image/img12.jpg)

![8](assets/image/img13.jpg)

### Challanges for future
When filtering on the German foreign ministry website, there is no link to the filter result. This makes it difficult to extract data quickly. The program cannot access documents with PDF extension. Open Refine is a very nice application, but web scraping can be done more easily with software languages such as Python requests or BeautifulSoap, which I researched while working on this project.
