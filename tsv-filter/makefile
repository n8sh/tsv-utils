APP_USES_LDC_PGO=2

include ../makedefs.mk

# tsv-filter has issues with LTO on OS X with xcode 9.3, LDC 1.8.0.
# LDC Issue 2585: https://github.com/ldc-developers/ldc/issues/2585
# Issues go beyond issue 2585 discussion. With xcode 9.3 all LTO fails.
# Fix by adding -disable-fp-elim to release_flags created by makedefs.mk.
# This was partially fixed in LDC 1.9.0, enough that the work-around is
# needed only for LDC 1.8.0.

ifeq ($(shell uname -s),Darwin)
	ifeq ($(compiler_type),ldc)
		ifeq ($(ldc_version),1.8.0)
			override release_flags += -disable-fp-elim
		endif
	endif
endif

include ../makeapp.mk

# No built-in unit tests
unittest: ;
unittest-codecov: ;
