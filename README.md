SIDFAX
======

This script allows you to send faxes through your Asterisk box.
It converts an email with either a PDF or TIFF attachment to an email with a *right*
TIFF format, and then passes it to Asterisk, which does the fax delivery.

Based on email2fax 1.2, originally written by Tomasz Chmielewski (http://wpkg.org/email2fax/), sidfax uses pdftops (xpdf) instead of pdf2ps (gs).

Sidfax was tested on VoiperOPEN 2.2.5 by SpheraIT.it based on CentOS 4.4 and Asterisk 1.4.42.


DEPENDENCIES
============

- munpack tool:	to decode MIME format mail messages
                If it doesn't work for you, try to get a binary for your system 
                at http://fr2.rpmfind.net (or any other rpm database).
                You can also download mpack/munpack sources from ftp://ftp.uu.net/networking/mail/mpack/
- gs:           to convert ps2tiff.
- pdftops:      xpdf 3.03 to convert pdf to ps
                http://www.foolabs.com/xpdf/download.html
- fetchmail:    to download email from your mailserver
- procmail:     to process email messages trough email2fax
- .fetchmailrc: configuration file for fetchmail.
- .procmailrc:  configuration file for procmail.
- digium fax application (http://www.digium.org) or soft-switch spandsp (http://www.soft-switch.org)


INSTALLATION
============

- install munpack tool
- install gs
- install xpdf >= 3.03
- install fetchmail
- install procmail
- find asterisk home directory: echo ~asterisk
- copy .fetchmailrc and .procmailrc to your homedirectory
- check .fetchmailrc and .procmailrc configuration
- edit configuration variables in email2fax
- copy email2fax in your bin directory eg: /usr/local/bin/
- add crontab line (crontab -e) to your local user to schedule fetchmail:

    eg, every minute: * * * * * /usr/bin/fetchmail -f /var/lib/asterisk/.fetchmailrc

	every 5 minutes: */5 * * * * /usr/bin/fetchmail -f /var/lib/asterisk/.fetchmailrc
	
- check your asterisk extensions.conf
- enjoy


FAQ
===
Q: xpdf: error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory

A: yum install xorg-x11-deprecated-libs.i386


CREDITS
=======
Pasquale 'sid' Fiorillo < info @ pasqualefiorillo . it > 2013

Tomasz Chmielewski < tch @ wpkg . org > 2005-2006
