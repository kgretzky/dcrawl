# dcrawl

dcrawl is a simple, but smart, multi-threaded web crawler for randomly gathering huge lists of unique domain names.

[![baby-gopher](https://raw.githubusercontent.com/drnic/babygopher-site/gh-pages/images/babygopher-badge.png)](http://www.babygopher.org)

![demo](https://raw.githubusercontent.com/kgretzky/dcrawl/master/img/dcrawl.gif)

## How it works?

dcrawl takes one site URL as input and detects all `<a href=...>` links in the site's body. Each found link is put into the queue. Successively, each queued link is crawled in the same way, branching out to more URLs found in links on each site's body.

How **smart crawling** works:
* Branching out only to predefined number of links found per one hostname.
* Maximum number of allowed different hostnames per one domain *(avoids subdomain crawling hell e.g. blogspot.com)*.
* Can be restarted with same list of domains - last saved domains are added to the URL queue.
* Crawls only sites that return *text/html* Content-Type in HEAD response.
* Retrieves site body of maximum 1MB size.
* Does not save inaccessible domains.

## How to run?

```
go build dcrawl.go
./dcrawl -url http://wired.com -out ~/domain_lists/domains1.txt -t 8
```

## Usage

```
     ___                          __
  __| _/________________ __  _  _|  |
 / __ |/ ___\_  __ \__  \\ \/ \/ /  |
/ /_/ \  \___|  | \// __ \\     /|  |__
\____ |\___  >__|  (____  /\/\_/ |____/
     \/    \/           \/       v.1.0

usage: dcrawl -url URL -out OUTPUT_FILE -t THREADS

  -ms int
        maximum different subdomains for one domain (def. 10) (default 10)
  -mu int
        maximum number of links to spider per hostname (def. 5) (default 5)
  -out string
        output file to save hostnames to
  -t int
        number of concurrent threads (def. 8) (default 8)
  -url string
        URL to start scraping from
  -v bool
        verbose (default false)
```

## License

dcrawl was made by [Kuba Gretzky](https://twitter.com/mrgretzky) from [breakdev.org](https://breakdev.org) and released under the MIT license.
