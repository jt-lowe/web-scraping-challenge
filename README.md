# Monash Data Course Wk 12 Assignment
## web-scraping-challenge

## Part 1 - Python/Jupyter Scraping

Using the provided URLs from the assignment doc, we had a browser opened and various data being pulled.

The news_title and news_p variables came from https://redplanetscience.com/, and the site was scraped with BeautifulSoup, the title was found in the html with the element "div" class "content_title" and the paragraph was found under "article_teaser_body", both .find() functions were followed with the .get_text() to pull the actual text out from the element.

The featured image was pulled using splinter from https://spaceimages-mars.com/, the process involved clicking on the "FULL SIZE" button, by utiliting the .find_by_partial_text() and .click() functions, then the source of the image was pulled using BeautifulSoup .find() function, where the image source was found within the class "fancybox-image" and the "src" was pulled by using square brackets to call/

The table data was expected to be called using pandas scraping, therefore we utilised the .read_html() function on the url https://galaxyfacts-mars.com/. Within this kenrel we print out the table a few times to ensure we are finding the correct data. The 0th table is pulled for the Mars facts, then we rename the columns from 0,1,2 to Description,Mars,Earth, using the .rename() function. The index is set to the Description column to finish off the formatting of the table. We then store the data as a varibale in html using the .to_html() function.

Finally, we access the url https://marshemispheres.com/ and use splinter to scrape the full sized hemisphere images. As we are repeating the same actions for each image, we can use a for loop, we can access the thumbnail link by using .find_by_css() and .click(), the we stow the title and image source into a dictionary, we then append the dictionary to an existing list so that we have one variable to hold all the information for all 4 images.


## Part 2 - Flask/MongoDB/HTML
The above Jupyter file was placed within a python file called mars_scraper, so it can be accessed by our app.py file. The returned dictionary contains each piece of data separately to make it easy to call within the html.

The app.py file is the Flask basis for our index.html, and utilises a connection to MongoDB to allow for display of our scraped data.

The html file was created to ensure a close recreation of the screenshot provided.
