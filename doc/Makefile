# Copyright (C) 2004-2022 Internet Systems Consortium, Inc. ("ISC")
# Copyright (c) 1995-2003 by Internet Software Consortium
#
# Permission to use, copy, modify, and distribute this software for any
# purpose with or without fee is hereby granted, provided that the above
# copyright notice and this permission notice appear in all copies.
#
# THE SOFTWARE IS PROVIDED "AS IS" AND ISC DISCLAIMS ALL WARRANTIES
# WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
# MERCHANTABILITY AND FITNESS.  IN NO EVENT SHALL ISC BE LIABLE FOR
# ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
# WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
# ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT
# OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
#
#   Internet Systems Consortium, Inc.
#   PO Box 360
#   Newmarket, NH 03857 USA
#   <info@isc.org>
#   https://www.isc.org/

all: References.txt References.html

References.txt: References.xml
	xml2txt References.xml

References.html: References.xml
	xml2html References.xml

devel:
	mkdir -p html
	doxygen devel/doxyfile > html/doxygen.log 2>html/doxygen-warnings.log

cppcheck:
	mkdir -p html
	cd .. && cppcheck --enable=all --inline-suppr \
          -f -v -j 2  -i tests/ -i dhcp-*/ \
          . 1> doc/html/cppcheck.log 2> doc/html/cppcheck-error.log

#       cppcheck can be extended with list of suppressions.
#          --suppressions-list=doc/cppcheck-skip.txt \


.PHONY: devel cppcheck