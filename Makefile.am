#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, version 2 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
AM_CFLAGS = -Wall -Werror
sbin_PROGRAMS = logrotate
logrotate_SOURCES = basenames.c config.c log.c logrotate.c \
		    basenames.h log.h logrotate.h queue.h

dist_man_MANS = logrotate.8 logrotate.conf.5

dist_noinst_DATA = logrotate.spec

EXTRA_DIST = ChangeLog.md README.md autogen.sh examples

# deprecated hard-wired Makefile, will be removed eventually
EXTRA_DIST += Makefile.legacy

# the dot ensures that logrotate is built before it is tested
SUBDIRS = . test

# for compatibility with older releases of logrotate
test: check

.PHONY: srpm rpm

rpm: srpm
	rpmbuild $(RPM_FLAGS) -ta $(distdir).tar.gz
srpm: dist
	rpmbuild $(RPM_FLAGS) -ts $(distdir).tar.gz
