# MTA Turnstile Data Scraper
Scrapes data from [MTA Turnstile data](http://web.mta.info/developers/turnstile.html) and dumps it into a SQLite database with matching column headers.

Supports older 2014 formats and converts them to the newer formats.

## Usage

```

python mta_main.py <db name> <start date: YYYY-MM-DD> <end date: YYYY-MM-DD>
```

Where `<db name>` is an empty database created by you. Data will be added to a table `entries`.

### To create an empty SQLite database

```
$ sqlite3 test.db 
sqlite > .database
sqlite > .exit
```

And `test.db` should now exist in your directory

### Example:

```
python mta_main.py mta_sept.db 2015-09-01 2015-09-30
```

## Output

For the lazy: [Sample data for September 2015](http://piratefsh.github.io/mta-turnstile-scraper/test/mta-turnstile-2015-sept.db)

Newer format.

```
id|CA|UNIT|SCP|STATION|LINENAME|DIVISION|DATE|TIME|DESC|ENTRIES|EXITS
1|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/19/2015|00:00:00|REGULAR|5317608|1797091
2|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/19/2015|04:00:00|REGULAR|5317644|1797096
3|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/19/2015|08:00:00|REGULAR|5317675|1797116
4|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/19/2015|12:00:00|REGULAR|5317778|1797215
5|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/19/2015|16:00:00|REGULAR|5318058|1797266
6|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/19/2015|20:00:00|REGULAR|5318468|1797316
7|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/20/2015|00:00:00|REGULAR|5318660|1797350
8|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/20/2015|04:00:00|REGULAR|5318695|1797359
9|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/20/2015|08:00:00|REGULAR|5318707|1797376
10|A002|R051|02-00-00|LEXINGTON AVE|NQR456|BMT|09/20/2015|12:00:00|REGULAR|5318797|1797443
```

Older 2014 format. Note that Station, Linename and Division data is missing
```
id|CA|UNIT|SCP|STATION|LINENAME|DIVISION|DATE|TIME|DESC|ENTRIES|EXITS
1|A002|R051|02-00-00||||01-22-12|11:00:00|REGULAR|3483225|1203166
2|A002|R051|02-00-00||||01-22-12|15:00:00|REGULAR|3483361|1203211
3|A002|R051|02-00-00||||01-22-12|19:00:00|REGULAR|3483557|1203265
4|A002|R051|02-00-00||||01-22-12|23:00:00|REGULAR|3483662|1203286
5|A002|R051|02-00-00||||01-23-12|03:00:00|REGULAR|3483688|1203294
6|A002|R051|02-00-00||||01-23-12|07:00:00|REGULAR|3483699|1203328
7|A002|R051|02-00-00||||01-23-12|11:00:00|REGULAR|3483843|1203659
8|A002|R051|02-00-00||||01-23-12|15:00:00|REGULAR|3484060|1203733
9|A002|R051|02-00-00||||01-23-12|19:00:00|REGULAR|3484866|1203815
10|A002|R051|02-00-00||||01-23-12|23:00:00|REGULAR|3485128|1203846
```

## Tests

Simple tests available for each source code file in the files themselves. Note `mta_db.py` needs a `test.db` to run tests.
