#***********************************************************************
#*                   GNU Lesser General Public License
#*
#* This file is part of the GFDL Flexible Modeling System (FMS).
#*
#* FMS is free software: you can redistribute it and/or modify it under
#* the terms of the GNU Lesser General Public License as published by
#* the Free Software Foundation, either version 3 of the License, or (at
#* your option) any later version.
#*
#* FMS is distributed in the hope that it will be useful, but WITHOUT
#* ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
#* FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
#* for more details.
#*
#* You should have received a copy of the GNU Lesser General Public
#* License along with FMS.  If not, see <http://www.gnu.org/licenses/>.
#***********************************************************************

# This is an automake file for the memutils directory of the FMS
# package.

# Ed Hartnett 2/22/19

# Include .h and .mod files.
AM_CPPFLAGS = -I${top_builddir}/.mod -I${top_srcdir}/include

# Build this uninstalled convenience library.
noinst_LTLIBRARIES = libfms_affinity.la libfms_affinity_c.la

# The convenience library depends on its source.
libfms_affinity_la_SOURCES = fms_affinity.F90
libfms_affinity_c_la_SOURCES = affinity.c

# Mod file depends on its .o file, is built and then installed.
fms_affinity_mod.mod: fms_affinity.lo

# Mod files are built and then installed as headers
MODFILES = fms_affinity_mod.mod
BUILT_SOURCES = $(MODFILES)
include_HEADERS = $(MODFILES)

SUFFIXES = .mod _mod.mod
.F90.mod:
	$(PPFCCOMPILE) -c $<
	@cp ${builddir}/$@ ${top_builddir}/.mod/
.F90_mod.mod:
	$(PPFCCOMPILE) -c $<
	@cp ${builddir}/$@ ${top_builddir}/.mod/

CLEANFILES = *.mod
