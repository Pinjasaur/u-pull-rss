# u-pull-rss

U Pull R Parts junkyard inventory scraped into RSS

## High Level

- https://simonwillison.net/2020/Oct/9/git-scraping/
- `curl 'https://upullrparts.com/wp-admin/admin-ajax.php' --compressed -X POST -H --data-raw 'action=getVehicles'`
- `npx -y @wcj/html-to-markdown-cli inventory.html -o . && mv -f inventory.html.md inventory.md`
- https://github.com/rtfpessoa/diff2html-cli
- https://github.com/janl/mustache.js

Thinking `inventory.html` for the response. And then `changelog/$YYYY-MM-DD.html` for each diff, which is used to build the RSS feed. Probably `0 9 * * *` for the cron, since 9am UTC is 3 or 4am CT depending on the time of year.

Diffing is more complicated than expected because it's common for the table rows to get reordered, so attempting to convert HTML table to Markdown table to keep each row a single line. From there, probably need to do some custom logic on added (`+`) lines versus removed (`-`) lines to see what was _actually_ added/removed versus simply reordered in the output.

This is preferable to the native GitHub RSS feed based on commits since it doesn't show the body of the diff, which is the most useful thing for this.
