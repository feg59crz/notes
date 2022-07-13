# HTML Head

## What is the head?
Part that is not displayed in the web browser.

Web browsers use information contained in the head to render the HTML.

## What it contains?
Contains information such as the page, links to CSS (if you choose to style your HTML content with CSS), links to custom favicons, and other metadata.

Contains **metadata** about the document.

## Elements
- `<title></title>`
- `<meta>`
    - `<meta charset="utf-8">` -> document's character encoding
    - `<meta name="" content="">`
        - `author`
        - `description`
        - `og:image` -> open graph image
        - `og:description` -> open graph description
        - `og:title` -> open graph title
        - `twitter:title` -> twitter cards
- `<link>`
    - `<link rel="" href="" type="">`
    - `<link rel="icon" href="favicon.ico" type="image/x-icon">` favicon
    - `<link rel="stylesheet" href="style.css">` -> stylesheet
- `<script></script>`
    - `<script src="main.js" defer></script>`
        - `defer` to load the JavaScript after the page has finished parsing the HTML.
        

    