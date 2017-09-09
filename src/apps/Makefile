APPS	= leandvb leansdrscan
APPS	+= leansdrcat leantsgen leanchansim leandvbtx

all:	$(APPS)

clean:
	rm -f $(APPS)

DEPS	= ../leansdr/*.h

CXXFLAGS	= -O3 -I.. -Wall -Wno-sign-compare -Wno-array-bounds -Wno-unused-variable -I/usr/X11R6/include -std=c++0x

%:	%.cc $(DEPS)
	/usr/local/Cellar/gcc/4.9.2_1/bin/g++-4.9 $(CXXFLAGS) -DGUI $< -lX11 -L/usr/X11R6/lib -o $@  ||  \
	/usr/local/Cellar/gcc/4.9.2_1/bin/g++-4.9 $(CXXFLAGS)       $<       -o $@

EMBED_FLAGS=	-I.. -Wall -Wno-sign-compare -Wno-array-bounds -Wno-unused-variable  \
		-Ofast -mfpu=neon -funsafe-math-optimizations -fsingle-precision-constant

leandvb.embedded:	leandvb.cc $(DEPS)
	g++ $(CXXFLAGS) $(EMBED_FLAGS) $< -static -o $@  ||  \
	g++ $(CXXFLAGS) $(EMBED_FLAGS) $<         -o $@
