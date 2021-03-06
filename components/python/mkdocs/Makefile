#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2016, Aurelien Larcher
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= mkdocs
COMPONENT_VERSION= 0.15.3
COMPONENT_REVISION= 2
COMPONENT_FMRI= library/python/mkdocs	
COMPONENT_CLASSIFICATION= Development/Python
COMPONENT_SUMMARY= mkdocs - Project documentation with Markdown
COMPONENT_PROJECT_URL= http://www.mkdocs.org/
COMPONENT_SRC= $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE= $(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	\
    sha256:a5442ae24fd9e6f9daeefaf354c960e5dac27ff388f63e1bb324ed8a1b7edaa9
COMPONENT_ARCHIVE_URL= \
    https://github.com/mkdocs/mkdocs/archive/$(COMPONENT_VERSION).tar.gz
COMPONENT_LICENSE= MkDocs License (BSD)

PYTHON_VERSIONS=	2.7

include $(WS_MAKE_RULES)/prep.mk
include $(WS_MAKE_RULES)/setup.py.mk
include $(WS_MAKE_RULES)/ips.mk

COMPONENT_POST_INSTALL_ACTION= \
  gfind $(PROTO_DIR)$(PYTHON_VENDOR_PACKAGES.32) -type f \
    -exec gawk '/^\#!.*python/{print FILENAME}{nextfile}' {} + \
  | xargs gsed -i -e '1 s;^.*$$;\#!$(PYTHON.32);'

build:		$(BUILD_NO_ARCH)

install:	$(INSTALL_NO_ARCH)

test:		$(NO_TESTS)

REQUIRED_PACKAGES += runtime/python-27
REQUIRED_PACKAGES += library/python/backports.ssl_match_hostname-27
REQUIRED_PACKAGES += library/python/click-27
REQUIRED_PACKAGES += library/python/jinja2-27
REQUIRED_PACKAGES += library/python/livereload-27
REQUIRED_PACKAGES += library/python/markdown-27
REQUIRED_PACKAGES += library/python/mkdocs-bootstrap-27
REQUIRED_PACKAGES += library/python/mkdocs-bootswatch-27
REQUIRED_PACKAGES += library/python/pyyaml-27
REQUIRED_PACKAGES += library/python/tornado-27
