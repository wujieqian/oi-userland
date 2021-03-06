#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2014 Alexander Pyhalov.  All rights reserved.
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= librsvg
COMPONENT_MAJOR_VERSION= 2.39
COMPONENT_VERSION= $(COMPONENT_MAJOR_VERSION).0
COMPONENT_FMRI= image/library/librsvg
COMPONENT_CLASSIFICATION= System/Multimedia Libraries
COMPONENT_SUMMARY= Library for SVG support for GNOME
COMPONENT_SRC= $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE= $(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= \
  sha256:aa47dcde0128eee6e3595d203bc673d9c27389588842f401bf585f31fc65095f
COMPONENT_ARCHIVE_URL= \
  http://ftp.gnome.org/pub/GNOME/sources/$(COMPONENT_NAME)/$(COMPONENT_MAJOR_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL= https://www.gnome.org/
COMPONENT_LICENSE= LGPLv2

include $(WS_MAKE_RULES)/prep.mk
include $(WS_MAKE_RULES)/configure.mk
include $(WS_MAKE_RULES)/ips.mk

PATH=$(PATH.gnu)

# Cloning is required for gmake test to pass
COMPONENT_PRE_CONFIGURE_ACTION = ($(CLONEY) $(SOURCE_DIR) $(@D))

CONFIGURE_SCRIPT= $(@D)/configure

COMPONENT_PREP_ACTION = ( cd $(@D) && aclocal && \
                          libtoolize --force --copy&&\
                          gtkdocize &&\
                          autoheader &&\
                          automake -a -f -c --gnu &&\
                          autoconf )

CONFIGURE_OPTIONS.32 = --sysconfdir=/etc
CONFIGURE_OPTIONS.64 = --sysconfdir=/etc/$(MACH64)
CONFIGURE_OPTIONS += --with-html-dir=/usr/share/gtk-doc/html/librsvg
CONFIGURE_OPTIONS += --disable-Bsymbolic
CONFIGURE_OPTIONS += --disable-static

COMPONENT_BUILD_ENV += CC="$(CC)"
COMPONENT_BUILD_ENV += CFLAGS="$(CFLAGS)"

build: $(BUILD_32_and_64)

install: $(INSTALL_32_and_64)

test: $(TEST_32_and_64)

# Auto-generated dependencies
REQUIRED_PACKAGES += library/desktop/cairo
REQUIRED_PACKAGES += library/desktop/gdk-pixbuf
REQUIRED_PACKAGES += library/desktop/gtk2
REQUIRED_PACKAGES += library/desktop/gtk3
REQUIRED_PACKAGES += library/desktop/pango
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/libcroco
REQUIRED_PACKAGES += library/libxml2
REQUIRED_PACKAGES += service/gnome/desktop-cache
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
