CILLY=cilly
COPTS=-Wno-attributes
CORO=../_build/corocheck.cma
# if CoroCheck has been installed, you can also use:
# CORO=corocheck

export CIL_FEATURES=

.PHONY: all clean FORCE
all: inference.pdf

FORCE:

inference.dot: inference.c FORCE
	$(CILLY) $(COPTS) --load=$(CORO) \
		--doCoroCheck --dotFile="$@" --save-temps --coopAttr=coroutine --blockAttr=blocking \
		-c $<

inference.pdf: inference.dot
	dot -Tpdf -o $@ $<

clean:
	rm -f *.o *.i *.cil.* *.dot *.pdf
