# Download eQSL.cc QSL images

This is a simple perl script to download eQSL.cc QSL images.  It has minimal
error checking, but seems to mostly function.

Please note: by retrieving these images, eQSL will automatically move your QSLs
from the *INBOX* to the *Archive*.  If keeping your inbox in its current state
is important to you, don't run this tool.

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

Currently the start year is hardcoded.  Please edit `esdl-download-images` if
you want to use a start year other than 2011.

State is stored in the `$HOME/.eqslcookies` file.  Please remove this file if
any kind of bad state is encountered.

## Execution

Image files will be saved in the current working directory.  Occasionally,
pages will be missing their images due to some kind of race condition in eQSL.
If you get a lot of missing images, you may wish to retry or manually download
those images.

Run as follows:

```
./eqsl-download-images
```

Example output:

```
$ ./eqsl-download-images
Logging in W1CALL...
retrieving QSLs..
2018-12 114 QSLs found
W1CALL-2017-01-15_08:06:00.0-N0XX-40m-SSB.png
W1CALL-2017-01-15_08:32:00.0-K7XXX-40m-SSB.png
W1CALL-2017-01-15_17:08:00.0-KC2XXX-40m-SSB.png
W1CALL-2017-01-15_19:58:00.0-KJ4XXX-40m-SSB.png
[...]
Expected 114 QSLs.  Found 112 images.
Pages missing images:
https://www.eqsl.cc/QSLCard/DisplayeQSL.cfm?Callsign=K2XXX&VisitorCallsign=W1CALL&QSODate=2017%2D06%2D14%2020%3A48%3A00%2E0&Band=2M&Mode=SSB
https://www.eqsl.cc/QSLCard/DisplayeQSL.cfm?Callsign=TI2XX&VisitorCallsign=W1CALL&QSODate=2017%2D09%2D08%2014%3A18%3A00%2E0&Band=20M&Mode=SSB
Done.
```

## TODO

1. Accept the start year on the command line
2. Handle multiple "accounts" for different QTHs with the same callsign
3. More error checking

