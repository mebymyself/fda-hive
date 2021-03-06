#/*
# *  ::718604!
# * 
# * Copyright(C) November 20, 2014 U.S. Food and Drug Administration
# * Authors: Dr. Vahan Simonyan (1), Dr. Raja Mazumder (2), et al
# * Affiliation: Food and Drug Administration (1), George Washington University (2)
# * 
# * All rights Reserved.
# * 
# * The MIT License (MIT)
# * 
# * Permission is hereby granted, free of charge, to any person obtaining
# * a copy of this software and associated documentation files (the "Software"),
# * to deal in the Software without restriction, including without limitation
# * the rights to use, copy, modify, merge, publish, distribute, sublicense,
# * and/or sell copies of the Software, and to permit persons to whom the
# * Software is furnished to do so, subject to the following conditions:
# * 
# * The above copyright notice and this permission notice shall be included
# * in all copies or substantial portions of the Software.
# * 
# * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
# * OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# * FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
# * DEALINGS IN THE SOFTWARE.
# */

PROGRAMS += dna-heptagon dna-heptagon-collect dna-heptagon-annotate profiler-concatenator

PROGRAMS_LIBS = -lviolib $(VLIB_LIB)
PROGRAMS_XLIBS = $(MYSQL_LIB)

dna-heptagon_SRCS = dna-heptagon.cpp
dna-heptagon-collect_SRCS = dna-heptagon-collect.cpp
dna-heptagon-annotate_SRCS = dna-heptagon-annotate.cpp
profiler-concatenator_SRCS = profiler-concatenator.cpp

ifeq ($(devdir),)
    devdir = $(abspath ../../..)
endif
include $(devdir)/build/makefile.meta

PNOHY: dist
dist:: dist_hept dist_hept_collect dist_hept_annotate

dist_hept:
	$(call dist-service-register,dna-heptagon,HIVE-heptagon Profiler,/Sequencing/)
	$(call dist-app,dna-heptagon,dna-heptagon)

dist_hept_collect:
	$(call dist-service-register,dna-heptagon-collect,HIVE-heptagon Profile Accumulator,/Sequencing/)
	$(call dist-app,dna-heptagon-collect,dna-heptagon-collect)


dist_hept_annotate:
	$(call dist-service-register,dna-heptagon-annotate,HIVE-heptagon Profile Annotator,/Annotate/)
	$(call dist-app,dna-heptagon-annotate,dna-heptagon-annotate)
