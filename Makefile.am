SUBDIRS = . tests

opdir = $(datadir)/vyatta-op/templates
share_perl5dir = $(datarootdir)/perl5/Vyatta
tmplscriptdir = $(datadir)/tmplscripts
yangdir = /usr/share/configd/yang
techsprtdir = $(datadir)/vyatta-op/functions/tech-support.d

bin_SCRIPTS = scripts/vyatta-show-bonding
bin_SCRIPTS += scripts/lacp-state
bin_SCRIPTS += scripts/lacp-op
sbin_SCRIPTS = scripts/vyatta-bonding
sysconf_DATA =
share_perl5_DATA = lib/Vyatta/Bonding.pm

AM_CFLAGS = -I /usr/include/vyatta-cfg

cpiop = find  . ! -regex '\(.*~\|.*\.bak\|.*\.swp\|.*\#.*\#\)' -print0 | \
  cpio -0pd

install-exec-hook:
	mkdir -p $(DESTDIR)$(opdir)
	cd templates && $(cpiop) $(DESTDIR)$(opdir) || true
	mkdir -p $(DESTDIR)$(tmplscritdir)
	cd tmplscripts && $(cpiop) $(DESTDIR)$(tmplscriptdir) || true
	mkdir -p $(DESTDIR)$(yangdir)
	cd yang && $(cpiop) $(DESTDIR)$(yangdir) || true
	mkdir -p $(DESTDIR)$(techsprtdir)
	cp scripts/0510-vyatta-interfaces-bonding $(DESTDIR)$(techsprtdir)
