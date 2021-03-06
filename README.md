# LMX-ot-NOSJ-Interchanging-Classic-Data-Formats-With-Single-blackmagic-Incantations

The details of the codeset and plots are included in the attached Microsoft Word Document (.docx) file in this repository. 
You need to view the file in "Read Mode" to see the contents properly after downloading the same.


Blackmagic Package - A Brief Introduction
==========================================

Automagically Convert ‘XML’ to ‘JSON’/‘JSON’ to ‘XML’

Description
============
Given a character string of ‘XML’, an ‘xml2’ or ‘XML’ package document, or a ‘URL’ to retrieve XML content from, convert said ‘XML’ to ‘JSON’ using the ‘xml-js’ ‘npm’ library https://www.npmjs.com/package/xml-js.Please reconsider your apparent desire to use this package.Automagic conversion of XML to JSON (or vice-versa) is rarely a good idea and a path fraught with peril. There are so many options to tweak to ensure you get what you think you want but likely truly want something else entirely, such as a more minimal extract of the original XML file.Seriously consider parsing the XML/JSON then using purrr idioms to extract the data you need into a proper list and then call jsonlite::toJSON() or xml2::as_xml_document() on said list.

What’s Inside The Tin
The following functions are implemented:

        xml_to_json: Convert XML to JSON
        json_to_xml: Convert JSON to XML

Installation
==============

    library(blackmagic)

    # current verison
    packageVersion("blackmagic")
    ## [1] '0.1.0'
    Sample (defaults)
    xml <- '<?xml version="1.0" encoding="utf-8"?>
    <note importance="high" logged="true">
        <title>Happy</title>
        <todo>Work</todo>
        <todo>Play</todo>
    </note>'

    cat(xml_to_json(xml))
    ## {"declaration":{"attributes":{"version":"1.0","encoding":"utf-8"}},"elements":[{"type":"element","name":"note","attributes":{"importance":"high","logged":"true"},"elements":[{"type":"element","name":"title","elements":[{"type":"text","text":"Happy"}]},{"type":"element","name":"todo","elements":[{"type":"text","text":"Work"}]},{"type":"element","name":"todo","elements":[{"type":"text","text":"Play"}]}]}]}
    Sample (xml2)
    cat(xml_to_json(xml2::read_xml(xml)))
    ## {"declaration":{"attributes":{"version":"1.0","encoding":"UTF-8"}},"elements":[{"type":"element","name":"note","attributes":{"importance":"high","logged":"true"},"elements":[{"type":"element","name":"title","elements":[{"type":"text","text":"Happy"}]},{"type":"element","name":"todo","elements":[{"type":"text","text":"Work"}]},{"type":"element","name":"todo","elements":[{"type":"text","text":"Play"}]}]}]}
    Sample (XML)
    cat(xml_to_json(XML::xmlParse(xml)))
    ## {"declaration":{"attributes":{"version":"1.0","encoding":"utf-8"}},"elements":[{"type":"element","name":"note","attributes":{"importance":"high","logged":"true"},"elements":[{"type":"element","name":"title","elements":[{"type":"text","text":"Happy"}]},{"type":"element","name":"todo","elements":[{"type":"text","text":"Work"}]},{"type":"element","name":"todo","elements":[{"type":"text","text":"Play"}]}]}]}
    Sample (URL + saner tweaks)
    cat(xml_to_json("https://httpbin.org/xml", spaces = 2, compact = FALSE, ignoreDeclaration = TRUE))
    ## {
    ##   "elements": [
    ##     {
    ##       "type": "comment",
    ##       "comment": "  A SAMPLE set of slides  "
    ##     },
    ##     {
    ##       "type": "element",
    ##       "name": "slideshow",
    ##       "attributes": {
    ##         "title": "Sample Slide Show",
    ##         "date": "Date of publication",
    ##         "author": "Yours Truly"
    ##       },
    ##       "elements": [
    ##         {
    ##           "type": "comment",
    ##           "comment": " TITLE SLIDE "
    ##         },
    ##         {
    ##           "type": "element",
    ##           "name": "slide",
    ##           "attributes": {
    ##             "type": "all"
    ##           },
    ##           "elements": [
    ##             {
    ##               "type": "element",
    ##               "name": "title",
    ##               "elements": [
    ##                 {
    ##                   "type": "text",
    ##                   "text": "Wake up to WonderWidgets!"
    ##                 }
    ##               ]
    ##             }
    ##           ]
    ##         },
    ##         {
    ##           "type": "comment",
    ##           "comment": " OVERVIEW "
    ##         },
    ##         {
    ##           "type": "element",
    ##           "name": "slide",
    ##           "attributes": {
    ##             "type": "all"
    ##           },
    ##           "elements": [
    ##             {
    ##               "type": "element",
    ##               "name": "title",
    ##               "elements": [
    ##                 {
    ##                   "type": "text",
    ##                   "text": "Overview"
    ##                 }
    ##               ]
    ##             },
    ##             {
    ##               "type": "element",
    ##               "name": "item",
    ##               "elements": [
    ##                 {
    ##                   "type": "text",
    ##                   "text": "Why "
    ##                 },
    ##                 {
    ##                   "type": "element",
    ##                   "name": "em",
    ##                   "elements": [
    ##                     {
    ##                       "type": "text",
    ##                       "text": "WonderWidgets"
    ##                     }
    ##                   ]
    ##                 },
    ##                 {
    ##                   "type": "text",
    ##                   "text": " are great"
    ##                 }
    ##               ]
    ##             },
    ##             {
    ##               "type": "element",
    ##               "name": "item"
    ##             },
    ##             {
    ##               "type": "element",
    ##               "name": "item",
    ##               "elements": [
    ##                 {
    ##                   "type": "text",
    ##                   "text": "Who "
    ##                 },
    ##                 {
    ##                   "type": "element",
    ##                   "name": "em",
    ##                   "elements": [
    ##                     {
    ##                       "type": "text",
    ##                       "text": "buys"
    ##                     }
    ##                   ]
    ##                 },
    ##                 {
    ##                   "type": "text",
    ##                   "text": " WonderWidgets"
    ##                 }
    ##               ]
    ##             }
    ##           ]
    ##         }
    ##       ]
    ##     }
    ##   ]
    ## }
    
Sample (some saner tweaks)

    '<?xml version="1.0" encoding="UTF-8"?>
    <bookstore>
      <book category="cooking">
        <title lang="en">Everyday Italian</title>
        <author>Giada De Laurentiis</author>
        <year>2005</year>
        <price>30.00</price>
      </book>
      <book category="children">
        <title lang="en">Harry Potter</title>
        <author>J K. Rowling</author>
        <year>2005</year>
        <price>29.99</price>
      </book>
      <book category="web">
        <title lang="en">Learning XML</title>
        <author>Erik T. Ray</author>
        <year>2003</year>
        <price>39.95</price>
      </book>
    </bookstore>' -> books

cat(xml_to_json(books, spaces = 2, compact = TRUE, ignoreDeclaration = TRUE))

    ## {
    ##   "bookstore": {
    ##     "book": [
    ##       {
    ##         "_attributes": {
    ##           "category": "cooking"
    ##         },
    ##         "title": {
    ##           "_attributes": {
    ##             "lang": "en"
    ##           },
    ##           "_text": "Everyday Italian"
    ##         },
    ##         "author": {
    ##           "_text": "Giada De Laurentiis"
    ##         },
    ##         "year": {
    ##           "_text": "2005"
    ##         },
    ##         "price": {
    ##           "_text": "30.00"
    ##         }
    ##       },
    ##       {
    ##         "_attributes": {
    ##           "category": "children"
    ##         },
    ##         "title": {
    ##           "_attributes": {
    ##             "lang": "en"
    ##           },
    ##           "_text": "Harry Potter"
    ##         },
    ##         "author": {
    ##           "_text": "J K. Rowling"
    ##         },
    ##         "year": {
    ##           "_text": "2005"
    ##         },
    ##         "price": {
    ##           "_text": "29.99"
    ##         }
    ##       },
    ##       {
    ##         "_attributes": {
    ##           "category": "web"
    ##         },
    ##         "title": {
    ##           "_attributes": {
    ##             "lang": "en"
    ##           },
    ##           "_text": "Learning XML"
    ##         },
    ##         "author": {
    ##           "_text": "Erik T. Ray"
    ##         },
    ##         "year": {
    ##           "_text": "2003"
    ##         },
    ##         "price": {
    ##           "_text": "39.95"
    ##         }
    ##       }
    ##     ]
    ##   }
    ## }
    
The other way ’round

cat(json_to_xml(jsonlite::toJSON(head(mtcars, 2)), spaces=2))

    ## <0>
    ##   <mpg>21</mpg>
    ##   <cyl>6</cyl>
    ##   <disp>160</disp>
    ##   <hp>110</hp>
    ##   <drat>3.9</drat>
    ##   <wt>2.62</wt>
    ##   <qsec>16.46</qsec>
    ##   <vs>0</vs>
    ##   <am>1</am>
    ##   <gear>4</gear>
    ##   <carb>4</carb>
    ##   <_row>Mazda RX4</_row>
    ## </0>
    ## <1>
    ##   <mpg>21</mpg>
    ##   <cyl>6</cyl>
    ##   <disp>160</disp>
    ##   <hp>110</hp>
    ##   <drat>3.9</drat>
    ##   <wt>2.875</wt>
    ##   <qsec>17.02</qsec>
    ##   <vs>0</vs>
    ##   <am>1</am>
    ##   <gear>4</gear>
    ##   <carb>4</carb>
    ##   <_row>Mazda RX4 Wag</_row>
    ## </1>
