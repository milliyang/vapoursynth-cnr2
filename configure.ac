AC_INIT([Cnr2], [1], [https://github.com/dubhater/vapoursynth-cnr2/issues], [Cnr2], [https://github.com/dubhater/vapoursynth-Cnr2/])

: ${CFLAGS=""}

AM_INIT_AUTOMAKE([foreign no-dist-gzip dist-xz subdir-objects no-define])
AM_SILENT_RULES([yes])

LT_INIT([disable-static win32-dll])

AC_PROG_CC

AC_CANONICAL_HOST


X86="false"

AS_CASE(
  [$host_cpu],
  [i?86],     [BITS="32" X86="true"],
  [x86_64],   [BITS="64" X86="true"],
)

AS_CASE(
   [$host_os],
   [cygwin*|mingw*],
   [
      AS_IF(
         [test "x$BITS" = "x32"],
         [
          AC_SUBST([PLUGINLDFLAGS], ["-Wl,--kill-at"])
         ]
      )
   ]
)


AS_IF(
      [test "x$X86" = "xtrue"],
      [
       AC_SUBST([MFLAGS], ["-mfpmath=sse -msse2"])
      ]
)

PKG_CHECK_MODULES([VapourSynth], [vapoursynth])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
