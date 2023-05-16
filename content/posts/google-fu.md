---
title: "Google Dorking (finding information) - OSINT"
date: 2022-02-25
tags: ["walkthrough"]
draft: false
---

> Everyone should learn how to search.

(*This post contains some google dorking techniques for finding information on the internet. Google is your friend.*)

- - -

## Searching

Narrow down search query, use **"\_something\_"**.<br>
Ex: `"Liverpool"`

For exact topic and site:

```
site: website-name topic-name

site: geekforgeeks sql
```

## Some terms

| **Term**      | **Action**                                                                        |
|:-------------:| --------------------------------------------------------------------------------- |
| `filetype:`   | search for a file by its extension                                                |
| `cache:`      | view <ins>google's cached version</ins> of a specified URL                        |
| `intitle:`    | the specified phrase *MUST* appear in the title of the page                       |
| `allintext:`  | searches specific text contained on any web page                                  |
| `allintitle:` | show pages that contain titles with X characters                                  |
| `allinurl:`   | used to fetch results whose URL contains all the specified characters             |
| `inurl:`      | useful for single keyword, same as `allinurl`                                     |
| `intitle:`    | used to search for various keywords inside the title                              |
| `inanchor:`   | useful when need to search for an exact anchor text used on any links.            |
| `intext:`     | useful to locate pages that contain characters or strings inside their text       |
| `site:`       | show the full list of all indexed URLs for the specified domain or sub-domain     |
| `*`           | wildcard used to search pages that contain *anything* before your word            |
| \|            | logical operator, will show all the sites which contain both words                |
| `+`           | used to concatenate words, useful to detect pages that use more than specific key |
| `-`           | used to avoiding showing results that contain certain words                       |

For example, searching for movies in online servers:

```
intitle:index of movie-name

intitle:index of? movie-name.mkv
```

## More examples

### Keyword `related`

To find similar websites, use `related:` <br>
Ex: `related:freecodecamp.org`

### Keyword `search:`

To search within a website, use `search:`d <br>
Ex: `search:freecodecamp.org web development`

### Keyword `...`

To search within a time-frame, use `...` <br>
Ex: `Developers 1992... 1999`

### Keyword `-`

To exclude a word, use `-` <br>
Ex: `Android Development -Flutter`

### Keyword `*`

To replace missing words, use `*` <br>
Ex: `*oriented programming in python`

### Keyword `define:`

To find a definition, use `define:` <br>
Ex: `define:object oriented programming`

### Keyword `" "`

To find exact phase, use `" "` <br>
Ex: `"python free tutorials"`

### Keyword `site:`

To search for a particular website or content, use `site:` <br>
Ex: `site: web dev blog`
