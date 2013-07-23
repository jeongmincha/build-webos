# Process this file with autoconf to produce a configure script.

# Copyright (c) 2008-2013 Hewlett-Packard Development Company, L.P.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

AC_INIT(webos, 0.0)
AC_PREREQ([2.61])
AC_COPYRIGHT([Copyright (c) 2008-2013 Hewlett-Packard Development Company, L.P.])
AC_CONFIG_SRCDIR([build-templates/mcf-status.in])

# customization
AC_MSG_CHECKING([customization])
case "$webos_customization" in
"") webos_customization_result="none" ;;
*)
	webos_customization_result=$webos_customization
	webos_customization_feature=":$webos_customization_result"
	;;
esac
AC_SUBST([customization], [$webos_customization])
AC_SUBST([customization_feature], [$webos_customization_feature])
AC_MSG_RESULT([$webos_customization_result])

# parallel_make
AC_MSG_CHECKING([parallel_make])
m4_define([webos_default_parallel_make], [1])
AC_ARG_ENABLE([parallel-make], [AS_HELP_STRING([--enable-parallel-make=N],
		     maximum number of tasks for each submake of bitbake to spawn (default: "webos_default_parallel_make"))],
		     [],
		     [enable_parallel_make="webos_default_parallel_make"])
case "$enable_parallel_make" in
     no|yes) enable_parallel_make=1 ;;
esac
AC_SUBST([parallel_make], [$enable_parallel_make])
AC_MSG_RESULT([$enable_parallel_make])

# bb_number_threads
AC_MSG_CHECKING([bb_number_threads])
m4_define([webos_default_bb_number_threads], [1])
AC_ARG_ENABLE([bb-number-threads], [AS_HELP_STRING([--enable-bb-number-threads=N],
		     maximum number of tasks for each submake of bitbake to spawn (default: "webos_default_bb_number_threads"))],
		     [],
		     [enable_bb_number_threads="webos_default_bb_number_threads"])
case "$enable_bb_number_threads" in
     no|yes) enable_bb_number_threads=1 ;;
esac
AC_SUBST([bb_number_threads], [$enable_bb_number_threads])
AC_MSG_RESULT([$enable_bb_number_threads])

# premirror
AC_MSG_CHECKING([premirror])
AC_ARG_ENABLE([premirror], [AS_HELP_STRING([--enable-premirror=PREMIRROR],
		     set PREMIRROR (default: none, own-mirrors class will not be used))],
                     [if test -z "$enableval"; then
                         enable_premirror_assignment=""
                         enable_premirror_inherit=""
                      else
                         enable_premirror_assignment="SOURCE_MIRROR_URL ?= \"$enableval\""
                         enable_premirror_inherit="INHERIT += \"own-mirrors\""
                      fi
                     ],
                     [ enable_premirror_assignment=""
                       enable_premirror_inherit=""
                     ])
AC_SUBST([premirror_assignment], [$enable_premirror_assignment])
AC_SUBST([premirror_inherit], [$enable_premirror_inherit])
AC_MSG_RESULT([$enableval])

# sstate mirror
AC_MSG_CHECKING([sstatemirror])
AC_ARG_ENABLE([sstatemirror], [AS_HELP_STRING([--enable-sstatemirror=SSTATE_MIRROR_URL],
                     set SSTATE_MIRROR_URL (default: none))],
                     [if test -z "$enableval"; then
                         enable_sstatemirror_assignment=""
                      else
                         enable_sstatemirror_assignment="SSTATE_MIRRORS ?= \" \\"
                         for URL in $enableval; do
                           echo "$URL" | grep "/PATH$" && AC_MSG_ERROR([$URL already ends with '/PATH', remove that])
                           echo "$URL" | grep "/$" && AC_MSG_ERROR([$URL ends with '/', remove that])
                           enable_sstatemirror_assignment="$enable_sstatemirror_assignment
  file://.* $URL/PATH \n \\"
                         done
                         enable_sstatemirror_assignment="$enable_sstatemirror_assignment
\""
                      fi
                     ],
                     [ enable_sstatemirror_assignment=""
                     ])
AC_SUBST([sstatemirror_assignment], [$enable_sstatemirror_assignment])
AC_MSG_RESULT([$enableval])

# network
AC_MSG_CHECKING([network])
AC_ARG_ENABLE([network], [AS_HELP_STRING([--enable-network],
		     enable network fetching (default: "True"))],
		     [case "$enableval" in
yes) enable_no_network="0" ;;
no) enable_no_network="1" ;;
esac],
		     [enable_no_network="0"])
AC_SUBST([no_network], [$enable_no_network])
AC_MSG_RESULT([$enable_network])

# fetch-premirror-only
AC_MSG_CHECKING([fetch_premirror_only])
AC_ARG_ENABLE([fetch_premirror_only], [AS_HELP_STRING([--enable-fetch-premirror-only],
		     fetch only from premirror (default: "False"))],
		     [case "$enableval" in
yes) enable_fetchpremirroronly="1" ;;
no) enable_fetchpremirroronly="0" ;;
esac],
		     [enable_fetchpremirroronly="0"])
AC_SUBST([fetchpremirroronly], [$enable_fetchpremirroronly])
AC_MSG_RESULT([$enable_fetchpremirroronly])

# generate-mirror-tarballs
AC_MSG_CHECKING([generate_mirror_tarballs])
AC_ARG_ENABLE([generate_mirror_tarballs], [AS_HELP_STRING([--enable-generate-mirror-tarballs],
		     generate tarballs suitable for mirroring (default: "False"))],
		     [case "$enableval" in
yes) enable_generatemirrortarballs="1" ;;
no) enable_generatemirrortarballs="0" ;;
esac],
		     [enable_generatemirrortarballs="0"])
AC_SUBST([generatemirrortarballs], [$enable_generatemirrortarballs])
AC_MSG_RESULT([$enable_generatemirrortarballs])

# private-internal-component-mirror
AC_MSG_CHECKING([private_internal_component_mirror])
AC_ARG_ENABLE([private_internal_component_mirror], [AS_HELP_STRING([--enable-private-internal-component-mirror],
		     enable private internal component mirror (default: "False"))],
		     [case "$enableval" in
yes) enable_privateinternalcomponentmirror="git://github.com/JeongMinCha" ;;
no) enable_privateinternalcomponentmirror="git://github.com/JeongMinCha" ;;
esac],
		     [enable_privateinternalcomponentmirror="git://github.com/JeongMinCha"])
AC_SUBST([privateinternalcomponentmirror], [$enable_privateinternalcomponentmirror])
AC_MSG_RESULT([$enableval])

# bitbake
AC_MSG_CHECKING([bitbake])
m4_define([bitbake_layer_location], ['${PALMDIR}/bitbake'])
m4_define([bitbake_default_bitbake], ['True'])
AC_ARG_ENABLE([bitbake], [AS_HELP_STRING([--enable-bitbake],
		     [configure to include bitbake (default: enabled)])],
		     [],
		     [enable_bitbake=bitbake_default_bitbake])
case "$enable_bitbake" in
     True|yes) enable_bitbake_layer=bitbake_layer_location ;;
     *) enable_bitbake_layer='' ;;
esac
AC_SUBST([bitbake], $enable_bitbake)
AC_SUBST([bitbake_layer], $enable_bitbake_layer)
AC_MSG_RESULT([$bitbake])

# oecore
AC_MSG_CHECKING([oecore])
m4_define([oecore_layer_location], ['${PALMDIR}/openembedded-core/meta'])
m4_define([oecore_default_oecore], ['True'])
AC_ARG_ENABLE([oecore], [AS_HELP_STRING([--enable-oecore],
		     [configure to include oecore (default: enabled)])],
		     [enable_oecore=$enableval],
		     [enable_oecore=oecore_default_oecore])
case "$enable_oecore" in
     no) enable_oecore_layer='' ;;
     *) enable_oecore_layer=oecore_layer_location ;;
esac
AC_SUBST([oecore], $enable_oecore)
AC_SUBST([oecore_layer], $enable_oecore_layer)
AC_MSG_RESULT([$oecore])

# webos
AC_MSG_CHECKING([webos])
m4_define([webos_layer_location], ['${PALMDIR}/meta-webos'])
m4_define([webos_default_webos], ['True'])
AC_ARG_ENABLE([webos], [AS_HELP_STRING([--enable-webos],
		     [configure to include webos (default: enabled)])],
		     [enable_webos=$enableval],
		     [enable_webos=webos_default_webos])
case "$enable_webos" in
     no) enable_webos_layer='' ;;
     *) enable_webos_layer=webos_layer_location ;;
esac
AC_SUBST([webos], $enable_webos)
AC_SUBST([webos_layer], $enable_webos_layer)
AC_MSG_RESULT([$webos])

# metaoe
AC_MSG_CHECKING([metaoe])
m4_define([metaoe_layer_location], ['${PALMDIR}/meta-openembedded/meta-oe'])
m4_define([webos_default_metaoe], ['True'])
AC_ARG_ENABLE([metaoe], [AS_HELP_STRING([--enable-metaoe],
		     [configure to include metaoe (default: enabled)])],
		     [enable_metaoe=$enableval],
		     [enable_metaoe=webos_default_metaoe])
case "$enable_metaoe" in
     no) enable_metaoe_layer='' ;;
     *) enable_metaoe_layer=metaoe_layer_location ;;
esac
AC_SUBST([metaoe], $enable_metaoe)
AC_SUBST([metaoe_layer], $enable_metaoe_layer)
AC_MSG_RESULT([$metaoe])

# buildhistory
AC_MSG_CHECKING([buildhistory])
AC_ARG_ENABLE([buildhistory], [AS_HELP_STRING([--enable-buildhistory],
		     enable buildhistory to check that versions are not going backward and content of images (default: "True"))],
		     [case "$enableval" in
yes) enable_buildhistory="1"; class_buildhistory="buildhistory" ;;
no) enable_buildhistory="0"; class_buildhistory="" ;;
esac],
		     [enable_buidhistory="1", class_buildhistory="buildhistory"])
AC_SUBST([buildhistory_enabled], [$enable_buildhistory])
AC_SUBST([buildhistory_class], [$class_buildhistory])
AC_MSG_RESULT([$enable_buildhistory])

AC_MSG_CHECKING([buildhistoryauthor])
AC_ARG_ENABLE([buildhistoryauthor], [AS_HELP_STRING([--enable-buildhistoryauthor="webos builder webos@builder.org"],
                     specify author to use in buildhistory git commits (default: none, will use author from git global config))],
                     [if test -z "$enableval"; then
                         enable_buildhistoryauthor_assignment=""
                      else
                         enable_buildhistoryauthor_assignment="BUILDHISTORY_COMMIT_AUTHOR ?= \"$enableval\""
                      fi
                     ],
                     [enable_buildhistoryauthor_assignment=""])
AC_SUBST([buildhistory_author], [$enable_buildhistoryauthor])
AC_SUBST([buildhistory_author_assignment], [$enable_buildhistoryauthor_assignment])
AC_MSG_RESULT([$enable_buildhistoryauthor])

AC_CONFIG_FILES([Makefile:build-templates/Makefile.in])
AC_CONFIG_FILES([bitbake.rc:build-templates/bitbake-rc.in])
AC_CONFIG_FILES([conf/bblayers.conf:build-templates/bblayers-conf.in])
AC_CONFIG_FILES([conf/local.conf:build-templates/local-conf.in])
AC_OUTPUT
