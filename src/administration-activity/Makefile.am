include $(top_srcdir)/Makefile.activity

install-activity:
	$(MAKE) -C $(top_srcdir)/boards
	cp $(top_srcdir)/boards/*.svg $(ACTIVITY_DESTDIR)/$(pkgdatadir)/boards/
	cp $(top_srcdir)/boards/*.xml $(ACTIVITY_DESTDIR)/$(pkgdatadir)/boards/

SUBDIRS = admin resources

pythondir = $(PYTHON_PLUGIN_DIR)

dist_python_DATA= 	administration.py



xmldir = $(pkgdatadir)/@PACKAGE_DATA_DIR@

xml_in_files = \
	administration.xml.in


xml_DATA = $(xml_in_files:.xml.in=.xml)

# Do not use the INTLTOOL_XML_RULE, we don't need to embed the translations
# in the file themselves. GCompris pick the translations from the po file at
# runtime.
#
$(xml_DATA): %.xml: %.xml.in
	sed -e "s/\(<\{1\}\/*\)_/\1/g" $< > $@

# Use this directive and instead of the one above to embed the translations
# in the xml files directly, this is needed for the tool gcompris2spip
#@INTLTOOL_XML_RULE@

CLEANFILES = $(xml_DATA)
EXTRA_DIST = ${xml_in_files} init_path.sh
