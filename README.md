# Simple DNS Plus knowledge base

The documentation contained in this repository is hosted at <https://simpledns.plus/kb>

## Contributions

Contributions are most welcome. No contribution is too big or too small.

Contributors will of course be attributed on our web-site. See the "Contributors" front-matter property below.

Fork this repository, clone locally, make your updates, commit, push, create a pull request in GitHub...

## Repository structure

- Topic files (markdown) are stored in the `docs` folder.  
The name of each topic file is: `<topic-ID>-<slug>.md` where
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

### Special HTML rendering (callouts / comments) (markdown only)

We use blockquotes (lines starting with ">") for special HTML rendering.

If you place one of the following tags following the first ">", the whole blockquote will be rendered / not rendered as follows:

| Tag | Blockquote rendering |
| --- | --- |
| `[!Note]`      | Light blue callout with "Note" header. For information without any special emphasis.| 
| `[!Tip]`       | Green callout with "Tip" header. For special tips and tricks or other helpful knowledge. | 
| `[!Important]` | Yellow callout with "Important" header. For stuff that requires cautions.  |
| `[!Warning]`   | Red callout with "Warning" header. Warn readers about situations that could cause data loss or unexpected consequences. |
| `[!Remark]` | Not rendered. For authoring remarks about source text. |
| `[!TODO]` | Not rendered. Remarks about stuff that still needs to be written. |

For example:

```
> [!Tip] Wash the car every sunday for best appearance
```

### Links

Note that bare URLs are NOT automatically converted into links.

### Copyright notice

All documents in this repository are Copyright &copy; JH Software.
