#
# configure.ac
#
# pool-dance: Simple, light-weight and efficient Bitcoin mining pool
#             <https://github.com/elima/pool-dance>
#
# Copyright (C) 2012, Eduardo Lima Mitev <elima@igalia.com>
#
# Authors:
#   Eduardo Lima Mitev <elima@igalia.com>
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU Affero General Public License
# version 3, or (at your option) any later version as published by
# the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# Affero General Public License at http://www.gnu.org/licenses/agpl.html
# for more details.
#

AC_PREREQ(2.59)

m4_define([prj_name],           [Pool Dance])
m4_define([prj_short_name],     [pool-dance])
m4_define([prj_home],           [https://github.com/elima/pool-dance])

m4_define([prj_version_major], [0])
m4_define([prj_version_minor], [1])
m4_define([prj_version_micro], [1])

m4_define([prj_version],
          [prj_version_major.prj_version_minor.prj_version_micro])

AC_INIT([prj_name],
	[prj_version],
	[prj_home])

AC_CONFIG_HEADERS(config.h)
AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE

PRJ_NAME="prj_short_name"
AC_SUBST(PRJ_NAME)

PRJ_VERSION="prj_version"
AC_SUBST(PRJ_VERSION)

# Check for programs
AC_PROG_LIBTOOL
AC_PROG_CC
AC_PROG_INSTALL
AM_PROG_CC_C_O

# Enable pkg-config
PKG_PROG_PKG_CONFIG

# Required libraries
PKG_CHECK_MODULES(EVD, evd-0.1 >= 0.1.24)

# Silent build
m4_ifdef([AM_SILENT_RULES],[AM_SILENT_RULES([yes])])

# Tests
AC_ARG_ENABLE(tests,
        AS_HELP_STRING([--enable-tests[=@<:@no/yes@:>@]],
                [Enable automated unit and functional tests [default=yes]]),,
                [enable_tests=yes])

AM_CONDITIONAL(ENABLE_TESTS, test x"${enable_tests}" = x"yes")

# Debug
AC_ARG_ENABLE(debug,
        AS_HELP_STRING([--enable-debug[=@<:@no/yes@:>@]],
                [Enable debug mode by adding -ggdb, -g3, -O0 and -Werror to CFLAGS [default=no]]),,
                [enable_debug=no])

AM_CONDITIONAL(ENABLE_DEBUG, test x"${enable_debug}" = x"yes")

# Output files
AC_OUTPUT([
	Makefile
        pool-dance/Makefile
])

echo ""
echo "   prj_name $VERSION"
echo "   ========================="
echo ""
echo "              Install prefix:   ${prefix}"
echo "      Enable automated tests:   ${enable_tests}"
echo ""
