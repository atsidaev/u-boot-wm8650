##########################################################################
#
#       Copyright Motorola, Inc. 1997
#       ALL RIGHTS RESERVED
#
#       You are hereby granted a copyright license to use, modify, and
#       distribute the SOFTWARE so long as this entire notice is retained
#       without alteration in any modified and/or redistributed versions,
#       and that such modified versions are clearly identified as such.
#       No licenses are granted by implication, estoppel or otherwise under
#       any patents or trademarks of Motorola, Inc.
#
#       The SOFTWARE is provided on an "AS IS" basis and without warranty.
#       To the maximum extent permitted by applicable law, MOTOROLA DISCLAIMS
#       ALL WARRANTIES WHETHER EXPRESS OR IMPLIED, INCLUDING IMPLIED
#       WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR
#       PURPOSE AND ANY WARRANTY AGAINST INFRINGEMENT WITH
#       REGARD TO THE SOFTWARE (INCLUDING ANY MODIFIED VERSIONS
#       THEREOF) AND ANY ACCOMPANYING WRITTEN MATERIALS.
#
#       To the maximum extent permitted by applicable law, IN NO EVENT SHALL
#       MOTOROLA BE LIABLE FOR ANY DAMAGES WHATSOEVER
#       (INCLUDING WITHOUT LIMITATION, DAMAGES FOR LOSS OF
#       BUSINESS PROFITS, BUSINESS INTERRUPTION, LOSS OF BUSINESS
#       INFORMATION, OR OTHER PECUNIARY LOSS) ARISING OF THE USE OR
#       INABILITY TO USE THE SOFTWARE.
#
############################################################################
TARGET = libi2o.a

#DEBUG  = -g
DEBUG   =
LST     = -Hanno -S
OPTIM   =
CC      = /risc/tools/pkgs/metaware/bin/hcppc
CFLAGS  = -Hnocopyr -c -Hsds -Hon=Char_default_unsigned -Hon=Char_is_rep -I../inc -I/risc/tools/pkgs/metaware/inc
CCobj   = $(CC) $(CFLAGS) $(DEBUG) $(OPTIM)
PREP    = $(CC) $(CFLAGS) -P

# Assembler used to build the .s files (for the board version)

ASOPT   = -big_si -c
ASDEBUG  = -l -fm
AS      = /risc/tools/pkgs/metaware/bin/asppc

# Linker to bring .o files together into an executable.

LKOPT	=  -Bbase=0 -Qn -q -r
LKCMD    =
LINK    =  /risc/tools/pkgs/metaware/bin/ldppc $(LKCMD) $(LKOPT)

# DOS Utilities

DEL     = rm
COPY    = cp
LIST    = ls

OBJECTS = i2o1.o i2o2.o

all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(LINK) $(OBJECTS) -o $@

objects: i2o1.o

clean:
	$(DEL) -f *.o *.i *.map *.lst $(TARGET) $(OBJECTS)

.s.o:
	$(DEL) -f $*.i
	$(PREP) -Hasmcpp $<
	$(AS) $(ASOPT) $*.i
#	$(AS) $(ASOPT) $(ASDEBUG) $*.i > $*.lst

.c.o:
	$(CCobj) $<

.c.s:
	$(CCobj) $(LST) $<

i2o1.o: i2o.h i2o1.c

i2o2.o: i2o.h i2o2.s
