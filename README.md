# u-pull-rss

[U Pull R Parts](https://upullrparts.com/) junkyard inventory scraped into RSS.

## How This Works

- Use the UPRP API to get the inventory as HTML, just like their website
  - `curl 'https://upullrparts.com/wp-admin/admin-ajax.php' --compressed -X POST --data-raw 'action=getVehicles'`
- Convert the HTML to Markdown, so each table row is a single line (makes diffing easier)
- Run a diff, deduplicating where necessary (reordered lines) to get the bare additions and removals
- Finesse that into a Markdown code fence as `diff` language stored in YYYY-MM-DD.md format
- Re-build the RSS feed on the fly, converting the Markdown into HTML for the feed item body

The RSS lives at [/feed.rss](./feed.rss). You'd put this URL into your feed reader of choice. If you want a recommendation, I use [Miniflux](https://miniflux.app/).

You can view the current inventory at [/inventory](./inventory).

## Who Built This?

Me. It's licensed under [MIT](https://pinjasaur.mit-license.org/2023).
