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

LIBRARIES += xlib

image.cpp_CXXFLAGS=$(IMAGEMAGICK_CFLAGS)

xlib_SRCS = zip.cpp md5.cpp xls2csv/Xls.cpp \
    $(if $(HAS_IMAGEMAGICK),image.cpp) \
    $(if $(HAS_LIBXLS),xls2csv/Workbook.cpp xls2csv/Worksheet.cpp) \
    $(if $(HAS_SQLITE3),sqlite.cpp)

ifeq ($(devdir),)
    devdir = $(abspath ../..)
endif
include $(devdir)/build/makefile.meta

.PHONY: dist
dist:: xlsx2csv/xlsx2csv.py
	$(call dist-src,qm,xlsx2csv.py,xlsx2csv/xlsx2csv.py)

xlsx2csv/xlsx2csv.py:
	@if which git &> /dev/null; then \
		git submodule update --init; \
	else \
		echo -e "\nPlease either install git and run 'git submodule update --init'"; \
		echo -e "or manually download xlsx2csv.py into vlib/xlib/xlsx2csv directory.\n"; \
	fi

