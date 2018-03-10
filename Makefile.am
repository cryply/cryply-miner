
if WANT_JANSSON
JANSSON_INCLUDES= -I$(top_srcdir)/compat/jansson
else
JANSSON_INCLUDES=
endif

EXTRA_DIST	= example-cfg.json nomacro.pl

SUBDIRS		= compat

bin_PROGRAMS	= minerd

dist_man_MANS	= minerd.1

AM_CFLAGS =	                   \
	$(GLOBAL_CFLAGS)           \
	$(AC_CFLAGS)               \
	$(JANSSON_INCLUDES)        \
	$(libcurl_CFLAGS)          \
	$(PTHREAD_FLAGS)

AM_LDFLAGS =                       \
	$(AC_LIBS)                 \
	$(JANSSON_LIBS)            \
	$(libcurl_LIBS)            \
	$(PTHREAD_LIBS)

minerd_SOURCES	= elist.h miner.h compat.h \
		  cpu-miner.c util.c \
		  sha2.c scrypt.c yescrypt.c
if USE_ASM
if ARCH_x86
minerd_SOURCES += sha2-x86.S scrypt-x86.S
endif
if ARCH_x86_64
minerd_SOURCES += sha2-x64.S scrypt-x64.S
endif
if ARCH_ARM
minerd_SOURCES += sha2-arm.S scrypt-arm.S
endif
endif
minerd_CFLAGS   = $(AM_CFLAGS)
minerd_LDADD	= $(AM_LDFLAGS)
