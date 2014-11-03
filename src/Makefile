TARGETS	= $(OBJDIR)framer
OBJDIR	=
PREFIX	= /usr/local
DESTDIR	=
BINDIR	= $(PREFIX)/bin
SBINDIR	= $(PREFIX)/sbin
CC	= cc
CPPFLAGSF=
CPPFLAGS= -I $(PREFIX)/include
CFLAGSF	= -W `pkg-config --cflags x11 gtk+-2.0`
CFLAGS	= -Wall -g -O2
LDFLAGSF= `pkg-config --libs x11 gtk+-2.0`
LDFLAGS	= -L$(PREFIX)/lib -Wl,-rpath,$(PREFIX)/lib
RM	= rm -f
LN	= ln -f
MKDIR	= mkdir -m 0755 -p
INSTALL	= install


all: $(TARGETS)

framer_OBJS = $(OBJDIR)framer.o $(OBJDIR)main.o
framer_CFLAGS = $(CPPFLAGSF) $(CPPFLAGS) $(CFLAGSF) $(CFLAGS)
framer_LDFLAGS = $(LDFLAGSF) $(LDFLAGS)

$(OBJDIR)framer: $(framer_OBJS)
	$(CC) -o $(OBJDIR)framer $(framer_OBJS) $(framer_LDFLAGS)

$(OBJDIR)framer.o: framer.c
	$(CC) $(framer_CFLAGS) -o $(OBJDIR)framer.o -c framer.c

$(OBJDIR)main.o: main.c
	$(CC) $(framer_CFLAGS) -o $(OBJDIR)main.o -c main.c

clean:
	$(RM) -- $(framer_OBJS)

distclean: clean
	$(RM) -- $(TARGETS)

install: $(TARGETS)
	$(MKDIR) $(DESTDIR)$(BINDIR)
	$(INSTALL) -m 0755 $(OBJDIR)framer $(DESTDIR)$(BINDIR)/framer

uninstall:
	$(RM) -- $(DESTDIR)$(BINDIR)/framer

.PHONY: all clean distclean install uninstall
