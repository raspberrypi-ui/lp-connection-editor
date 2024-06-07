desktopdir=$(datadir)/applications

desktop_in_files= \
	lp-connection-editor.desktop.in \
	$(NULL)
desktop_DATA = $(desktop_in_files:.desktop.in=.desktop)
@INTLTOOL_DESKTOP_RULE@

EXTRA_DIST = $(desktop_in_files) \
			$(desktop_DATA) \
			$(NULL)
