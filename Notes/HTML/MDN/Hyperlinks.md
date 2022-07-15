# HTML - Hyperlinks

## What is a hyperlink?

Hyperlinks allow us to link documents to other documents or resources, link to specific parts of documents, or make apps available at a web address.

  

## Anatomy of a link

```html

<a href="https://www.mozilla.org/en-US/">the Mozilla homepage</a>.

```

  

## Aditional information

```html

<a href="https://www.mozilla.org/en-US/"

title="The best place to find more information about Mozilla's

mission and how to contribute">the Mozilla homepage</a>.

```

  

## Document Fragments

```html

<h2 id="Mailing_address">Mailing address</h2>

  
  

<p>The <a href="#Mailing_address">company mailing address</a> can be found at the bottom of this page.</p>

  

```

  

## Download Atribute

```html

<p>The <a href="#Mailing_address">company mailing address</a> can be found at the bottom of this page.</p>

```

  

## Emails

```html

<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>

  

<a href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&subject=The%20subject%20of%20the%20email&body=The%20body%20of%20the%20email">

Send mail with cc, bcc, subject and body

</a>

```