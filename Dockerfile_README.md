# Dcrawl

## Source

https://github.com/kgretzky/dcrawl
 
## Usage
```bash
cd dcrawl/
docker build -t dcrawl .
docker run -it dcrawl:latest
```
## Help
```bash
     ___                          __   
  __| _/________________ __  _  _|  |  
 / __ |/ ___\_  __ \__  \\ \/ \/ /  |  
/ /_/ \  \___|  | \// __ \\     /|  |__
\____ |\___  >__|  (____  /\/\_/ |____/
     \/    \/           \/       v.1.0

Usage of ./dcrawl:
  -ms int
    	maximum different subdomains for one domain (def. 10) (default 10)
  -mu int
    	maximum number of links to spider per hostname (def. 5) (default 5)
  -out string
    	output file to save hostnames to

```
