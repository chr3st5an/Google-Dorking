# Google Dorking

## Table Of Contents

- [Advanced Searching](#advanced-searching)

- [Search Operators](#search-operators)

- [Simple Examples](#simple-examples)

- [Finding Valuable Information](#finding-valuable-information)

- [Further](#further)

- [Meta](#meta)

---

## Advanced Searching

Google Dorking describes the process of using advanced search filters that allow to retrieve more efficient results. It is a technique often used by cybersecurity professionals in order to find valuable information about a target. While Google Dorking itself is legal (in most countries), it might quickly lead to actions that aren't, such as visiting a site with illegal content in it. Hence using [TOR](https://www.torproject.org/) or a [VPN](https://privacyguides.org/vpn/) is recommended. It is also beneficial to use a search aggregator like [SearX](https://searx.github.io/searx/).

---

## Search Operators

| Operator         | Description                                                                                                              | Syntax                               | Example                           |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------ | --------------------------------- |
| ()               | Group multiple terms or operators. Allows advanced expressions                                                           | (&lt;term> or &lt;operator>)         | inurl:(html \| php)               |
| *                | Wildcard. Matches any word                                                                                               | &lt;text> * &lt;text>                | How to * a computer               |
| ""               | The given keyword has to match exactly. *case-insensitive*                                                               | "&lt;keywords>"                      | "google"                          |
| m..n / m...n     | Search for a range of numbers. *n* should be greater than *m*                                                            | &lt;number>..&lt;number>             | 1..100                            |
| -                | Documents that match the operator are excluded. *NOT*-Operator                                                           | -&lt;operator>                       | -site:youtube.com                 |
| +                | Include documents that match the operator                                                                                | +&lt;operator>                       | +site:youtube.com                 |
| \|               | Logical *OR-Operator*. Only one operator needs to match in order for the overall expression to match                     | &lt;operator> \| &lt;operator>       | "google" \| "yahoo"               |
| ~                | Search for synonyms of the given word. Not supported by Google                                                           | ~&lt;word>                           | ~book                             |
| @                | Perform a search only on the given social media platform. Rather use **site**                                            | @&lt;socialmedia>                    | @instagram                        |
| after            | Search for documents published / indexed after the given date                                                            | after:&lt;yy(-mm-dd)>                | after:2020-06-03                  |
| allintitle       | Same as **intitle** but allows multiple keywords seperated by a space                                                    | allintitle:&lt;keywords>             | allintitle:dog cat                |
| allinurl         | Same as **inurl** but allows multiple keywords seperated by a space                                                      | allinurl:&lt;keywords>               | allinurl:search com               |
| allintext        | Same as **intext** but allows multiple keywords seperated by a space                                                     | allintext:&lt;keywords>              | allintext:math science university |
| AROUND           | Search for documents in which the first word is up to *n* words away from the second word and vice versa                 | &lt;word1> AROUND(&lt;n>) &lt;word2> | google AROUND(10) good            |
| author           | Search for articles written by the given author if applicable                                                            | author:&lt;name>                     | author:Max                        |
| before           | Search for documents published / indexed before the given date                                                           | before:&lt;yy(-mm-dd)>               | before:2020-06-03                 |
| cache            | Search on the cached version of the given website. Uses Google's cache to do so                                          | cache:&lt;domain>                    | cache:google.com                  |
| contains         | Search for documents that link to the given fileype. Not supported by Google                                             | contains:&lt;filetype>               | contains:pdf                      |
| date             | Search for documents published within the past *n* months. Not supported by Google                                       | date:&lt;number>                     | date:3                            |
| define           | Search for the definition of the given word                                                                              | define:&lt;word>                     | define:funny                      |
| ext              | Search for a specific filetype                                                                                           | ext:&lt;documenttype>                | ext:pdf                           |
| filetype         | Refer to **ext**                                                                                                         | filetype:&lt;documenttype>           | filetype:pdf                      |
| inanchor         | Search for the given keyword in a website's anchors                                                                      | inanchor:&lt;keyword>                | inanchor:security                 |
| index of         | Search for documents containing direct downloads                                                                         | index of:&lt;term>                   | index of:mp4 videos               |
| info             | Search for information about a website                                                                                   | info:&lt;domain>                     | info:google.com                   |
| intext           | Keyword needs to be in the text of the document                                                                          | intext:&lt;keyword>                  | intext:news                       |
| intitle          | Keyword needs to be in the title of the document                                                                         | intitle:&lt;keyword>                 | intitle:money                     |
| inurl            | Keyword needs to be in the URL of the document                                                                           | inurl:&lt;keyword>                   | inurl:sheet                       |
| link / links     | Search for documents whose links contain the given keyword. Useful for finding documents that link to a specific website | link:&lt;keyword>                    | link:google                       |
| location         | Show documents based on the given location                                                                               | location:&lt;location>               | location:USA                      |
| numrange         | Refer to **m..n**                                                                                                        | numrange:&lt;number>-&lt;number>     | numrange:1-100                    |
| OR               | Refer to **\|**                                                                                                          | &lt;operator> OR &lt;operator>       | "google" OR "yahoo"               |
| phonebook        | Search for related phone numbers associated with the given name                                                          | phonebook:&lt;name>                  | phonebook:"william smith"         |
| relate / related | Search for documents that are related to the given website                                                               | relate:&lt;domain>                   | relate:google.com                 |
| safesearch       | Exclude adult content such as pornographic videos                                                                        | safesearch:&lt;keyword>              | safesearch:sex                    |
| source           | Search on a specific news site. Rather use **site**                                                                      | source:&lt;news>                     | source:theguardian                |
| site             | Search on the given site. Given argument might also be just a TLD such as **com, net**, etc                              | site:&lt;domain>                     | site:google.com                   |
| stock            | Search for information about a market stock                                                                              | stock:&lt;stock>                     | stock:dax                         |
| weather          | Search for information about the weather of the given location                                                           | weather:&lt;location>                | weather:Miami                     |

[[Back to top]](#table-of-contents)

---

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

> Search for websites published before 2020 which have the TLD `.gov`, are either html or php documents and contain the words "homework", "teacher" and "school"

```dork
@instagram chr3st5an
```

> Search for the term "chr3st5an" on instagram

[[Back to top]](#table-of-contents)

---

## Finding Valuable Information

```dork
intitle:"webcamXP 5" | inurl:"lvappl.htm"
```

> Find open/public webcams

```dork
intext:password ext:log
```

> Find log documents wich have the string "password" in it

```dork
inurl:/proc/self/cwd
```

> Find vulnerable webservers

```dork
inurl:email.xls ext:xls
```

> Find excel documents that contain email addresses

```dork
index of:mp3 intext:.mp3
```

> Find mp3 (music) documents

[[Back to top]](#table-of-contents)

---

## Further

You can find more Google Dorks at the [exploit-db](https://www.exploit-db.com/google-hacking-database)

[[Back to top]](#table-of-contents)

---

## Meta

##### License

The information provided here are dedicated to the public domain. Use them as you wish.

[[Back to top]](#table-of-contents)
