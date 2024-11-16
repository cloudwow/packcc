CC=gcc
CFLAGS_D=-std=gnu89 -fsigned-char -Wall -Wextra -Wno-unused-parameter -Wno-overlength-strings -pedantic -O0 -g2
CFLAGS_R=-std=gnu89 -fsigned-char -Wall -Wextra -Wno-unused-parameter -Wno-overlength-strings -pedantic -O2 -DNDEBUG
LDFLAGS_D=
LDFLAGS_R=

ROOTDIR=../..
SRCDIR=$(ROOTDIR)/src
TMPDIR_D=debug/tmp
TMPDIR_R=release/tmp
BINDIR_D=debug/bin
BINDIR_R=release/bin

EXAMPLES:=$(patsubst $(EXDIR)/%.peg,examples/%,$(wildcard $(EXDIR)/*.peg))

BINS= \
  $(BINDIR_D)/packcc \
  $(BINDIR_R)/packcc \
  $(patsubst %,$(BINDIR_D)/%,$(EXAMPLES)) \
  $(patsubst %,$(BINDIR_R)/%,$(EXAMPLES))


.PHONY: all check clean


all: $(BINS)

$(BINDIR_D)/packcc: $(SRCDIR)/packcc.c
	mkdir -p $(dir $@) && $(CC) $(CFLAGS_D) -o $@ $< $(LDFLAGS_D)

$(BINDIR_R)/packcc: $(SRCDIR)/packcc.c
	mkdir -p $(dir $@) && $(CC) $(CFLAGS_R) -o $@ $< $(LDFLAGS_R)


clean:
	rm -f $(BINS) 
