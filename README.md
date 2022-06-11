![Author](https://img.shields.io/badge/Author-chr3st5an-purple.svg)

<div style="text-align:center;">

<h1>Google Dorking</h1>

</div>

## Advanced Searching

Google Dorking describes the process of using advanced search filters that allow to retrieve more efficient results. It's a technique often used by hackers in order to find valuable information about a target. While Google Dorking itself is legal, it might quickly lead to actions that aren't. Hence using [TOR](https://www.torproject.org/) or a [VPN](https://privacyguides.org/vpn/) is recommended. 

## Search Operators

| Operator   | Description                                                                                        | Syntax                               | Example                           |
| ---------- | -------------------------------------------------------------------------------------------------- | ------------------------------------ | --------------------------------- |
| ()         | Group multiple terms or operators                                                                  | (&lt;term> or &lt;operator>)         | inurl:(html \| php)               |
| *          | Wildcard. Matches any word                                                                         | &lt;text> * &lt;text>                | How to * a computer               |
| ""         | The given keyword has to **match exactly**. Case insensitive                                       | "&lt;keywords>"                      | "google"                          |
| m..n       | Search for a **range of numbers**; m &lt;= n                                                       | &lt;number>..&lt;number>             | 1..100                            |
| -          | Files that match the operator are **excluded**                                                     | -&lt;operator>                       | -site:youtube.com                 |
| +          | Include files that match the operator                                                              | +&lt;operator>                       | +site:youtube.com                 |
| \|         | Logical **OR**                                                                                     | &lt;operator> \| &lt;operatorer>     | "google" \| "yahoo"               |
| ~          | Search for synonyms of the given word                                                              | ~&lt;word>                           | ~book                             |
| @          | Perform a search only on the given social media platform                                           | @&lt;socialmedia>                    | @instagram                        |
| after      | Search for files released after the given date                                                     | after:&lt;yy(-mm-dd)>                | after:2020-06-03                  |
| allintitle | Same as **intitle** but allows multiple keywords seperated by a space                              | allintitle:&lt;keywords>             | allintitle:dog cat                |
| allinurl   | Same as **inurl** but allows multiple keywords seperated by a space                                | allinurl:&lt;keywords>               | allinurl:search com               |
| allintext  | Same as **intext** but allows multiple keywords seperated by a space                               | allintext:&lt;keywords>              | allintext:math science university |
| AROUND     | Search for files in which the first word is up to *n* words away from the second word & vice versa | &lt;word1> AROUND(&lt;n>) &lt;word2> | google AROUND(10) good            |
| author     | Search for articles written by the given author if applicable                                      | author:&lt;name>                     | author:Max                        |
| before     | Search for files published before the given date                                                   | before:&lt;yy(-mm-dd)>               | before:2020-06-03                 |
| cache      | Search on the cached version of the given website. Uses Google's cache                             | cache:&lt;domain>                    | cache:google.com                  |
| contains   | Search for files that link to the given filetype                                                   | contains:&lt;filetype>               | contains:pdf                      |
| date       | Search for files published within the past *n* months                                              | date:&lt;number>                     | date:3                            |
| define     | Search for the definition of a word                                                                | define:&lt;word>                     | define:funny                      |
| ext        | Search for a specific file type                                                                    | ext:&lt;filetype>                    | ext:pdf                           |
| filetype   | Same as **ext**                                                                                    | -                                    | -                                 |
| inanchor   | Search for the given keyword in a website's anchors                                                | inanchor:&lt;keyword>                | inanchor:security                 |
| index of   | Search for files containing direct downloads                                                       | index of:&lt;term>                   | index of:mp4 videos               |
| info       | Retrieve information about a website                                                               | info:&lt;domain>                     | info:google.com                   |
| intext     | Keyword needs to be in the text                                                                    | intext:&lt;keyword>                  | intext:news                       |
| intitle    | Keyword needs to be in the title                                                                   | intitle:&lt;keyword>                 | intitle:money                     |
| inurl      | Keyword needs to be in the URL                                                                     | inurl:&lt;keyword>                   | inurl:sheet                       |
| link       | Find files whose links contain the keyword                                                         | link:&lt;keyword>                    | link:google                       |
| location   | Show files based on the given location                                                             | location:&lt;location>               | location:USA                      |
| OR         | Same as **\|**                                                                                     | -                                    | -                                 |
| phonebook  | Search for related phone numbers of the given name                                                 | phonebook:&lt;name>                  | phonebook:max                     |
| relate     | Search for files that are **related to** the given site                                            | relate:&lt;domain>                   | relate:google.com                 |
| safesearch | Exclude adult content                                                                              | safesearch:&lt;keyword>              | safesearch:sex                    |
| source     | Search on a specific source                                                                        | source:&lt;news>                     | source:theguardian                |
| site       | Search on the given site. Given arg migth also be just a TLD                                       | site:&lt;domain>                     | site:google.com                   |
| stock      | Retrieve information of a market stock                                                             | stock:&lt;stock>                     | stock:dax                         |
| weather    | Show information about the weather of the given location                                           | weather:&lt;location>                | weather:Miami                     |

## Simple Examples

```dork
"google" 1..100
```

> Search for websites that contain the word "google" and a number between 1 and 100

```dork
Videos -site:youtube.*
```

> Search for the term "Videos" but exclude results from YouTube

```dork
How to * a computer after:2022-01-01
```

> Search for websites published after the 1st January 2022 dealing about how to `use/repair/shutdown/...` a computer

```dork
allintext:homework teacher school site:gov before:2020 ext:(html | php)
```

> Search for websites published before 2020 which have the TLD `.gov`, are either html or php files and contain the words "homework", "teacher" and "school"

```dork
@instagram chr3st5an
```

> Search for the term "chr3st5an" on instagram

## Finding Valuable Information

```dork
intitle:”webcamXP 5” | inurl:"lvappl.htm"
```

> Find open/public webcams

```dork
intext:password ext:log
```

> Find log files wich have the string "password" in it

```dork
inurl:/proc/self/cwd
```

> Find vulnerable webservers

```dork
inurl:email.xls ext:xls
```

> Find excel files that contain email addresses

```dork
index of:mp3 intext:.mp3
```

> Find mp3 (music) files 
