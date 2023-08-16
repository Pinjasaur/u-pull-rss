# u-pull-rss

U Pull R Parts junkyard inventory scraped into RSS

## High Level

- https://simonwillison.net/2020/Oct/9/git-scraping/
- `curl 'https://upullrparts.com/wp-admin/admin-ajax.php' --compressed -X POST -H --data-raw 'action=getVehicles'`
- https://github.com/rtfpessoa/diff2html-cli
- https://github.com/janl/mustache.js

Thinking `inventory.html` for the response. And then `changelog/$datestring.html` for each diff, which is used to build the RSS feed.

This is preferable to the native GitHub RSS feed based on commits since it doesn't show the body of the diff, which is the most useful thing for this.
