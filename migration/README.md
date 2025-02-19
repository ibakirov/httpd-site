# CMS Migration

1. Observations

   - tools/announce.sh requires many changes to update md files in git
   - several dev pages including release.md, devnotes.md, and index.md refer to the ASF CMS and will require updates
   - httpd/site/trunk/docs has already moved, but the documentation mentions it
   - various places refer to mbox archives which are now 404
   - left navigation could use right margin/padding for some long links like `Apache Traffic Control`

2. Markdown conversions

   - Rename all mdtext files as md files
   - Headings with {#link} needed the # between title and annotation removed
   - Definition lists are no longer supported. Made appropriate changes
   - Converted many httpd.apache.org links to internal links
   - Modified most <pre> and <blockquote> to markdown auto or explicit fenced code blocks
   - Improved dev/patches layout
   - Assorted other changes

   See [changes.txt](changes.txt)

3. Theme Template

   - CMS templates were converted into `base.html`
   - markdown is no longer allowed within the templates. mdtext parts are copied in as html.
   - Flood leftnav is controlled via metadata on page
   - Copyright year is automatically updated to the current year of the build

4. Configuration

   See [pelicanconf.py](../pelicanconf.py)

5. Pelican ASF plugin configuration

   [asfgenid.py](../theme/plugins/asfgenid.py)

   - 'unsafe_tags': True  # allow style, script, and iframe tags
   - 'metadata': False    # no metadata replacement in markdown files
   - 'elements': True     # use mdx_elementid features
   - 'headings': True     # Fix up headings w/ permalinks
   - 'headings_re': r'^h[1-4]'
   - 'permalinks': True,
   - 'toc': False         # does not use [TOC]
   - 'toc_headers': r"h[1-4]",
   - 'tables': True       # Fix up for markdown table class
