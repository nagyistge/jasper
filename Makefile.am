# Copyright (c) 2001-2003 Michael David Adams.
# All rights reserved. 

# __START_OF_JASPER_LICENSE__
# 
# JasPer License Version 2.0
# 
# Copyright (c) 2001-2006 Michael David Adams
# Copyright (c) 1999-2000 Image Power, Inc.
# Copyright (c) 1999-2000 The University of British Columbia
# 
# All rights reserved.
# 
# Permission is hereby granted, free of charge, to any person (the
# "User") obtaining a copy of this software and associated documentation
# files (the "Software"), to deal in the Software without restriction,
# including without limitation the rights to use, copy, modify, merge,
# publish, distribute, and/or sell copies of the Software, and to permit
# persons to whom the Software is furnished to do so, subject to the
# following conditions:
# 
# 1.  The above copyright notices and this permission notice (which
# includes the disclaimer below) shall be included in all copies or
# substantial portions of the Software.
# 
# 2.  The name of a copyright holder shall not be used to endorse or
# promote products derived from the Software without specific prior
# written permission.
# 
# THIS DISCLAIMER OF WARRANTY CONSTITUTES AN ESSENTIAL PART OF THIS
# LICENSE.  NO USE OF THE SOFTWARE IS AUTHORIZED HEREUNDER EXCEPT UNDER
# THIS DISCLAIMER.  THE SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS
# "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING
# BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A
# PARTICULAR PURPOSE AND NONINFRINGEMENT OF THIRD PARTY RIGHTS.  IN NO
# EVENT SHALL THE COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, OR ANY SPECIAL
# INDIRECT OR CONSEQUENTIAL DAMAGES, OR ANY DAMAGES WHATSOEVER RESULTING
# FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT,
# NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION
# WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.  NO ASSURANCES ARE
# PROVIDED BY THE COPYRIGHT HOLDERS THAT THE SOFTWARE DOES NOT INFRINGE
# THE PATENT OR OTHER INTELLECTUAL PROPERTY RIGHTS OF ANY OTHER ENTITY.
# EACH COPYRIGHT HOLDER DISCLAIMS ANY LIABILITY TO THE USER FOR CLAIMS
# BROUGHT BY ANY OTHER ENTITY BASED ON INFRINGEMENT OF INTELLECTUAL
# PROPERTY RIGHTS OR OTHERWISE.  AS A CONDITION TO EXERCISING THE RIGHTS
# GRANTED HEREUNDER, EACH USER HEREBY ASSUMES SOLE RESPONSIBILITY TO SECURE
# ANY OTHER INTELLECTUAL PROPERTY RIGHTS NEEDED, IF ANY.  THE SOFTWARE
# IS NOT FAULT-TOLERANT AND IS NOT INTENDED FOR USE IN MISSION-CRITICAL
# SYSTEMS, SUCH AS THOSE USED IN THE OPERATION OF NUCLEAR FACILITIES,
# AIRCRAFT NAVIGATION OR COMMUNICATION SYSTEMS, AIR TRAFFIC CONTROL
# SYSTEMS, DIRECT LIFE SUPPORT MACHINES, OR WEAPONS SYSTEMS, IN WHICH
# THE FAILURE OF THE SOFTWARE OR SYSTEM COULD LEAD DIRECTLY TO DEATH,
# PERSONAL INJURY, OR SEVERE PHYSICAL OR ENVIRONMENTAL DAMAGE ("HIGH
# RISK ACTIVITIES").  THE COPYRIGHT HOLDERS SPECIFICALLY DISCLAIM ANY
# EXPRESS OR IMPLIED WARRANTY OF FITNESS FOR HIGH RISK ACTIVITIES.
# 
# __END_OF_JASPER_LICENSE__

AUTOMAKE_OPTIONS = foreign

EXTRA_DIST = README INSTALL COPYRIGHT LICENSE NEWS ChangeLog data doc \
  jasper.spec.in jasper.spec ac_aux

ACLOCAL_AMFLAGS = -I ac_m4

# Note: We need to put the derived file "jasper.spec" in the distribution
# in order to facilitate RPM building.

SUBDIRS = src pkgconfig

rpm: dist
	for i in BUILD RPMS SRPMS SOURCES SPECS; do \
		j=$$PWD/RPMTOP/$$i; \
		if ! -d $$j; then \
			mkdir -p $$j || exit 1; \
		fi \
	done
	rpmbuild  --rmsource --define "_topdir $$PWD/RPMTOP" \
	  -ta $(PACKAGE)-$(JAS_VERSION).tar.gz
	rm -rf $$PWD/RPMTOP/BUILD/$(PACKAGE)-$(JAS_VERSION)

@GENERATE_CHANGELOG_RULES@
dist-hook: dist-ChangeLog

# We need to ensure that any Subversion directories in the extra directories
# are removed before the distribution archive is made.
#dist-hook:
#	for i in $(EXTRA_DIST); do \
#		if test -d $$i; then \
#			j=`find $(distdir)/$$i -name .svn`; \
#			if test -n "$$j"; then \
#				rm -rf $$j; \
#			fi; \
#		fi; \
#	done

