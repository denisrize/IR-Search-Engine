# IR-Search-Engine
### Description:
Wikipedia Search Engine over more than 6 million pages that been implemented using Flask-based RESTful API. The engine efficiently searches and retrieves relevant information from a preprocessed and indexed collection of over 6 million articles. These articles are categorized into buckets using multiple methods, ensuring swift and accurate search results. The search engine supports multiple endpoints to search articles based on different criteria, providing titles, IDs, and other relevant data. It boasts an average response time of 2.6 seconds and achieves a 67% success rate in searches (recall).

![googleImage](https://user-images.githubusercontent.com/55393990/220896173-a43911a9-0498-4b7a-ab71-1157c5e89e6d.png)

### Features:
- Fast and Efficient: Returns results in an average of 2.6 seconds.
- High Recall: Achieves a 67% successful search rate.
- Multiple Search Methods: Supports binary search, BM25, and cosine similarity.
- Versatile Endpoints: Includes endpoints for body search, title search, anchor text search, PageRank, and page views.

### Endpoints

| Endpoint           | Description                                                                                      |
|--------------------|--------------------------------------------------------------------------------------------------|
| /search_body       | Returns up to 100 search results for the query using TF-IDF and cosine similarity based on the body of articles. |
| /search_title      | Returns all search results containing a query word in the title, ordered by the number of distinct query words appearing in the title. |
| /search_anchor     | Returns all search results containing a query word in the anchor text of articles, ordered by the number of query words in the anchor text. |
| /get_pagerank      | Returns PageRank values for a list of provided Wikipedia article IDs.                             |
| /get_pageview      | Returns the number of page views for each of the provided Wikipedia articles in August 2021.      |

## General Functionality

The process for each search endpoint involves the following steps:

1. **Tokenization**: The query or text is tokenized using a provided tokenizer.
2. **Stopword Removal**: Stopwords are removed from the tokenized text to focus on meaningful terms.
3. **Scoring and Ranking**: Depending on the endpoint:
    - **/search_body**: Computes TF-IDF scores and uses cosine similarity to rank documents.
    - **/search_title** and **/search_anchor**: Ranks documents based on the number of distinct or total query words.
4. **Retrieval**: The relevant documents are retrieved and returned as search results.

For the PageRank and PageView endpoints:
- **/get_pagerank**: Computes and returns PageRank values for the given article IDs.
- **/get_pageview**: Retrieves and returns the number of page views for the specified articles.
