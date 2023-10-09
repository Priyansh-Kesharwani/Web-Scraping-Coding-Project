# Web Scraper

This project is designed to scrape content from web pages and save it to a JSON file.

## `scrape_page()`

The `scrape_page()` method is responsible for scraping a single page:

- It makes a GET request to the page URL to download the HTML content.
- BeautifulSoup parses the HTML into a navigable DOM structure.
- The `<title>` tag text is extracted as the page title.
- The main content div is identified by id="content," and its text is extracted.
- Unwanted DOM elements like sidebars are removed using lists of unwanted classes and tags.
- Tables are converted from HTML to Markdown format using markdownify.
- The page title, cleaned content text, and URL are returned as a dictionary.

## `get_total_pages()`

The `get_total_pages()` helper method finds the total number of pagination links on the first page:

- It requests the base URL, parses the HTML, and finds all "page-numbers" links.
- The length of this list is returned as the total page count.

## `scrape_new_pages()`

This method handles scraping multiple pages:

- It takes the base URL, the number of pages to scrape, and a data directory.
- Existing scraped data is loaded from the JSON file.
- It iterates from 1 to the page limit, calling `scrape_page()` on each page.
- The scraped page data is added to a list, and new URLs are tracked to avoid duplicates.
- Finally, all data is written to the JSON file.

This allows for scraping an entire site by recursively calling with higher page limits.

Overall, this project provides a simple web scraper to extract content from multiple pages into a JSON dataset.
