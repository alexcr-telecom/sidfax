SIDFAX
======

This script allows you to send faxes through your Asterisk box.
It converts an email with either a PDF or TIFF attachment to an email with a *right*
TIFF format, and then passes it to Asterisk, which does the fax delivery.

Based on email2fax 1.2, original written by Tomasz Chmielewski (http://wpkg.org/email2fax/), sidfax use pdftops (xpdf) instead of pdf2ps (gs).

Sidfax was tested on VoiperOPEN 2.2.5 by SpheraIT.it based on CentOS 4.4 and Asterisk 1.4.42.


DEPENDENCIES
============

- munpack tool:	for decoding MIME format mail messages
                If it doesn't work for you, try to get a binary for your system 
                at http://fr2.rpmfind.net (or any other rpm database).
                You can also download mpack/munpack sources from ftp://ftp.uu.net/networking/mail/mpack/
- gs:           for convert ps2tiff.
- pdftops:      xpdf 3.03 for convert pdf to ps
                http://www.foolabs.com/xpdf/download.html
- fetchmail:    for download email from your mailserver
- procmail:     for process email messages trough email2fax
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
- create a local user for sidfax eg: useradd -g asterisk sidfax
- copy .fetchmailrc and .procmailrc to your homedirectory
- check .fetchmailrc and .procmailrc configuration
- edit configuration variables in email2fax
- copy email2fax in your bin directory eg: /usr/local/bin/
- add crontab line (crontab -e) to your local user for schedule fetchmail running.

    eg, for every minutes: * * * * * /usr/bin/fetchmail -f /home/sidfax/.fetchmailrc

	  for every 5 minutes: */5 * * * * /usr/bin/fetchmail -f /home/sidfax/.fetchmailrc
	
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
