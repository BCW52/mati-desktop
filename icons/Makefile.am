
iconsdir = $(datadir)/icons/hicolor

png_icons = \
	16x16/apps/mati-desktop.png \
	22x22/apps/mati-desktop.png \
	24x24/apps/mati-desktop.png \
	32x32/apps/mati-desktop.png \
	48x48/apps/mati-desktop.png \
	128x128/apps/mati-desktop.png

nobase_dist_icons_DATA = \
	$(png_icons) \
	scalable/apps/mati-desktop.svg \
	scalable/apps/mati-desktop-symbolic.svg

gtk_update_icon_cache = gtk-update-icon-cache -f -t $(datadir)/icons/hicolor

EXTRA_DIST = \
	meson.build

.PHONY: build-png-icons clean-png-icons

install-data-hook: update-icon-cache
uninstall-hook: update-icon-cache
update-icon-cache:
	@-if test -z "$(DESTDIR)"; then \
		echo "Updating Gtk icon cache."; \
		$(gtk_update_icon_cache); \
	else \
		echo "*** Icon cache not updated.  After (un)install, run this:"; \
		echo "***   $(gtk_update_icon_cache)"; \
	fi

if HAVE_RSVG_CONVERT
build-png-icons:
	$(RSVG_CONVERT) -w 16 -h 16 scalable/apps/mati-desktop.svg -o 16x16/apps/mati-desktop.png
	$(RSVG_CONVERT) -w 22 -h 22 scalable/apps/mati-desktop.svg -o 22x22/apps/mati-desktop.png
	$(RSVG_CONVERT) -w 24 -h 24 scalable/apps/mati-desktop.svg -o 24x24/apps/mati-desktop.png
	$(RSVG_CONVERT) -w 32 -h 32 scalable/apps/mati-desktop.svg -o 32x32/apps/mati-desktop.png
	$(RSVG_CONVERT) -w 48 -h 48 scalable/apps/mati-desktop.svg -o 48x48/apps/mati-desktop.png
	$(RSVG_CONVERT) -w 128 -h 128 scalable/apps/mati-desktop.svg -o 128x128/apps/mati-desktop.png
endif

clean-png-icons:
	rm -f $(png_icons)
