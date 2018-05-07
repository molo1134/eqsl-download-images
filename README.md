# Download eQSL.cc QSL images

This is a simple perl script to download eQSL.cc QSL images.  It has minimal
error checking, but seems to mostly function.

Please note: by retrieving these images, eQSL will automatically move your QSLs
from the *INBOX* to the *Archive*.  **If keeping your inbox in its current
state is important to you, don't run this tool.**

## Copyright and License

Copyright (c) 2018, molo1134

[2-Clause BSD License](LICENSE)

## Requirements

Debian/Ubuntu linux packages:
* perl
* liburi-perl
* curl

Windows 7 using Cygwin packages:

* [cygwin](https://www.cygwin.com/)
* perl
* perl-URI
* curl

## Configuration

Create a file in `$HOME/.eqsllogin` with the following content:

```
login_callsign="YOURCALL"
login_password="yourpass"
```

State is stored in the `$HOME/.eqslcookies` file.  Please remove this file if
any kind of bad state is encountered.

## Execution

Image files will be saved in the current working directory.  Occasionally,
pages will be missing their images due to some kind of race condition in eQSL.
If you get a lot of missing images, you may wish to retry or manually download
those images.

Run as follows:

```
./eqsl-download-images [start_year] [end_year]
```

Default `start_year` is 2000.  Default `end_year` is the current calendar year.

Example, retrieving just 2017 QSLs:

```
$ ./eqsl-download-images 2017 2017
Logging in W1CALL...
retrieving QSLs..
2017-12 114 QSLs found
W1CALL-20170115_0806-N0XX-40m-SSB.png
W1CALL-20170115_0832-K7XXX-40m-SSB.png
W1CALL-20170115_1708-KC2XXX-40m-SSB.png
W1CALL-20170115_1958-KJ4XXX-40m-SSB.png
[...]
Expected 114 QSLs.  Found 112 images.
Pages missing images:
https://www.eqsl.cc/QSLCard/DisplayeQSL.cfm?Callsign=K2XXX&VisitorCallsign=W1CALL&QSODate=2017%2D06%2D14%2020%3A48%3A00%2E0&Band=2M&Mode=SSB
https://www.eqsl.cc/QSLCard/DisplayeQSL.cfm?Callsign=TI2XX&VisitorCallsign=W1CALL&QSODate=2017%2D09%2D08%2014%3A18%3A00%2E0&Band=20M&Mode=SSB
Done.
```

## TODO

1. Handle multiple "accounts" for different QTHs with the same callsign
2. More error checking

