# Simple DNS Plus knowledge base

The documentation contained in this repository is hosted at <https://support.simpledns.plus/kb>

## Contributions

Contributions are most welcome. No contribution is too big or too small.

Contributors will of course be attributed on our web-site. See the "Contributors" front-matter property below.

Fork this repository, clone locally, make your updates, commit, push, create a pull request in GitHub...

## Repository structure

- Topic files (markdown) are stored in the `docs` folder.  
The name of each topic file is: `<topic-ID>_<slug>.md` where
  - `<topic-ID>` - an integer value assigned sequentially.
  - `<slug>` - a string closely matching the topic's title but with URL friendly characters (replace spaces and special characters with hyphens, etc.). Used as part of the topic's URL.
- A `_category.cfg` file (in the `docs` folder) lists category IDs and corresponding category names separated by a space (simple one line per item file). The listed order is not significant (sorted by category name later).

## Document structure

### Front-matter

At the top of each topic file is a section with meta data. This section starts and ends with with three dashes (---) on a line by itself.
In other similar documentation projects, this section is in YAML format.
That is also the plan for this project, but it we haven't gotten to that just yet.
For now it is just a line based collection of properties - one property per line.
Each line consisting of a key value pair.

```
---
<key>: <value>
<key>: <value>
---
# <title>
<markdown>
```

Required properties: 
 
- **Category:** Integer value indicating the category that the topic belongs to (see `categories` file above).

Optional properties:  

- **FrontPage:** `true` - list on knowledge base front page.
- **VGroup:** An article version group identifier (fx `WINVER`) that is shared between multiple topic files - enabling an "article version selector" at the top of the page. 
- **VName:** Article version name/number for this topic (fx `Windows Server 2016`) - will appear in the article version selector (see above).
- **VSort:** Integer value indicating sort order of this topic in the article version group (see above). 
- **References:** Comma separated list of topic-IDs (numbers only). Renders as a list of links at the bottom of the page.
- **Contributors:** Comma separated list of GitHub IDs of contributors  
- **Notes:** Notes / remarks.

### Document title

After the front-matter section, there must be exactly one H1 header (#) with the title of the document.


### Links

Note that bare URLs are NOT automatically converted into links.