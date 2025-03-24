# Ceneo Scraper
class version of the ceneo scraper

productID: 161123001
## Algorithm for extracting opinions about single product from Ceneo.pl
1. Make an HTTP request to ceno.pl/{productID}
2. If response is OK (200-399) we parse the html into DOM structure
3. Extract opinions and their components from the DOM structure
4. Assign opinions with their components to complex data structures
5. If there are more pages, extract opinions from them (repeat steps 1-5)
6. Save data structures with opinions into database

## Structure of a single opinion in Ceneo.pl
|Component|Variable|Selector|
|----------|----------|----------|
|opinion|opinion||
|opinion ID|opinion_id|div.user-post user-post__card js_product-review[data-entry-id]|
|opinion’s author|author|span.user-post__author-name|
|author’s recommendation|recommendation|span.user-post__author-recomendation > em.recommended|
|score expressed in number of stars|score|span.user-post__score-count|
|opinion’s content|content|div.user-post__text|
|list of product advantages|pros|div.review-feature__section > div.review__section-title > div.review-feature__item review-feature__item--positive|
|list of product disadvantages|cons|review-feature__section > div.review__section-title > div.review-feature__item review-feature__item--negative|
|how many users think that opinion was helpful|thumbs_up|div.js_product-review-usefulness vote > div.vote-yes js_product-review-vote js_vote-yes[data-total-vote]|
|how many users think that opinion was unhelpful|thumbs_down|div.js_product-review-usefulness vote > div.vote-no js_product-review-vote js_vote-no[data-total-vote]|
|publishing date|date_published||
|purchase date|date_purchased||