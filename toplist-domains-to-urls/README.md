# toplist-domains-to-urls

This directory contains the code used to convert domains into URLs that can be crawled.

 - `check-availability.py` attempts to connect to all domains in a `rank,domain` 
   Tranco toplist csv passed via stdin, 
   both with and without HTTPS and with and without `www.` prefix. 
   Results are stored in a SQLite database. 
   Run repeatedly to accomodate temporary service disruptions.
 - `export-urls.py` accepts the same `rank,domain` toplist via stdin and 
   outputs a `rank,url` csv file.

## Requirements

This code has been tested with Python 3.9.4 and the requirements listed in `requirements.txt`.

## Example Usage

```bash
python3 --version  # should be 3.9 or above
pip install -r requirements.txt
curl -o tranco.csv https://tranco-list.eu/download/K8JW/1000
cat tranco.csv | ./check-availability.py
cat tranco.csv | ./export-urls.py > urls.csv
```
