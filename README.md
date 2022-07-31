# hardenedtmpfiles


This is a fork from opentmpfiles, a standalone utility written to process 
systemd-style tmpfiles.d
files so that they can be handled on systems with or without systemd
installed.

Hardened changes prevent removal or change of ownership when directories 
are owned by root. 

Race conditions reported in CVE-2017-18925 are prevented by first deleting
the directory recursively and then creating a new one with mkdir. If the 
destination is created before mkdir, the command will fail. 

Under the principle of "better fail than corrupt", his script will
exit on any error.

For more information on the files this utility can process, see the
[tmpfiles.d man page][1].

[1]: https://www.freedesktop.org/software/systemd/man/tmpfiles.d.html
