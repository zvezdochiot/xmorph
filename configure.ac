dnl Process this file with autoconf to produce a configure script.

dnl################################
dnl : ACGM : this part was generated by glade

AC_INIT(xmorph,20060817,mennucc1@debian.org)
dnl configure.ac

dnl ACGM: the following line tells PRCS (and CVS?) to update the version
dnl $Format: "AM_INIT_AUTOMAKE(xmorph, $ProjectVersion$)"$
AM_INIT_AUTOMAKE(xmorph, 20060817)

AM_CONFIG_HEADER(config.h)
AC_CONFIG_SRCDIR([config.h.in])

GETTEXT_PACKAGE=xmorph
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE,"$GETTEXT_PACKAGE",[ the gettext environment ])


# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S
dnl AC_PROG_MAKE_SET
dnl AC_PROG_RANLIB obsoleted by AC_PROG_LIBTOOL
dnl AC_PROG_YACC

dnl I am not using any of these, but I should
dnl AC_HEADER_STDC
AC_CHECK_HEADERS([libintl.h locale.h malloc.h memory.h stdlib.h string.h strings.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
dnl AC_HEADER_STDBOOL
AC_C_CONST
AC_C_INLINE
AC_TYPE_SIZE_T

# Checks for library functions.
dnl AC_FUNC_REALLOC
AC_FUNC_STAT
LDFLAGS='-lm'
AC_CHECK_FUNCS([atexit floor getcwd memmove memset sqrt strdup strerror strrchr])




dnl ####################  -with-*, 


AC_ARG_WITH(morph,         [  --with-morph         compile morph  (yes)])

AC_ARG_WITH(xmorph,        [  --with-xmorph        compile xmorph (auto)])

AC_ARG_WITH(gtk,           [  --with-gtk=1,2       use GTK 1 or 2 (auto)])

if ! test "x$with_gtk" = "x1" -o   "x$with_gtk" = "x2" -o "x$with_gtk" = "x" ; then
  AC_ERROR([wrong argument --with-gtk=$with_gtk   use  1 or 2])
fi
AC_ARG_WITH(gtkmorph,      [  --with-gtkmorph      compile gtkmorph (auto)])

AC_ARG_WITH(tkmorph,       [  --with-tkmorph       compile tkmorph (no)])


######################################################## waili

AC_ARG_WITH(waili,         [  --with-waili         link gtkmorph with Waili wavelet library])

if  test "x$with_gtk" = "x1" ; then
  AC_MSG_WARN([ Sorry,  Waili linking code needs newer gtk/glib ])
  with_waili=no
fi

if test "x$with_waili" = x  -o "x$with_waili" = xyes ; then 
 AC_LANG_PUSH(C++)
 dnl AC_CHECK_LIB([waili], [Image(10,10)])
 AC_CHECK_HEADERS(waili/Image.h,  [
   with_waili=yes
 ], [
 if test "x$with_waili" = xyes ; then
  AC_MSG_ERROR([ The  Waili wavelet library was not found  ])
  exit 1
 else
  AC_MSG_WARN([ Sorry, no Waili was found  ])
  with_waili=no
 fi
 ])
 AC_LANG_POP(C++)
fi
AM_CONDITIONAL(COND_WAILI, test "x$with_waili" != xno )	
if test "x$with_waili" != xno ; then
 AC_DEFINE(HAVE_WAILI, 1,[use code that links to Waili wavelet library] )
else
 AC_DEFINE(HAVE_WAILI, 0,[use code that links to Waili wavelet library] )
fi
######################################################## fftw

AC_ARG_WITH(fftw,         [  --with-fftw          link gtkmorph with libfftw3   (superfast FFT )])

if test "x$with_fftw" = x  -o "x$with_fftw" = xyes ; then 
 AC_CHECK_HEADERS(fftw3.h,  [
   with_fftw=yes
 ], [
 if test "x$with_fftw" = xyes ; then
  AC_MSG_ERROR([ The FFTW3 library was not found  ])
  exit 1
 else
  AC_MSG_WARN([ Sorry, no libfftw  was found : FFT will be very slow ])
  with_fftw=no
 fi
 ])
fi
AM_CONDITIONAL(COND_FFTW, test "x$with_fftw" != xno )	
if test "x$with_fftw" != xno ; then
 AC_DEFINE(HAVE_FFTW, 1,[use code that links to fftw3 library] )
else
 AC_DEFINE(HAVE_FFTW, 0,[use code that links to fftw3 library] )
fi

########################################################





#if test x$target = xi386-cygwin ; then
# export CC=i386-
#else 


dnl AC_ISC_POSIX
dnl AC_PROG_CC
dnl AM_PROG_CC_STDC
dnl AC_HEADER_STDC

AM_PROG_LIBTOOL

dnl Add the languages which your application supports here.
ALL_LINGUAS="it fr"
AM_GNU_GETTEXT([external]) 


dnl Work around stupid definition (note the quotes!!)
dnl if test "x${datadir}" = 'x${prefix}/share'; then
dnl   AC_MSG_WARN([ Work around stupid setting of datadir="'$datadir'" ])
dnl   if test "x${prefix}" = "xNONE"; then
dnl     d="${ac_default_prefix}/share"
dnl   else
dnl     d="${prefix}/share"
dnl  fi
dnl  else
dnl   d="${datadir}"
dnl fi

dnl Set PACKAGE_DATA_DIR in config.h.
dnl NO ! use DATADIR "/" PACKAGE
dnl    where  DATADIR is set it in  gtkmorph/Makefile.am
dnl l=$d/${PACKAGE}
dnl AC_DEFINE_UNQUOTED(PACKAGE_DATA_DIR, $l, [ data dir ])

dnl Set PACKAGE_LOCALE_DIR in config.h.
dnl NO ! use LOCALEDIR, and set it in  gtkmorph/Makefile.am
dnl l=$d/locale
dnl AC_DEFINE_UNQUOTED(PACKAGE_LOCALE_DIR,$l , [ locale dir ])


dnl Set PACKAGE_SOURCE_DIR in config.h.
dnl packagesrcdir=`cd $srcdir && pwd`
dnl AC_DEFINE_UNQUOTED(PACKAGE_SOURCE_DIR, "${packagesrcdir}", [ source dir ])

dnl Use -Wall if we have gcc.
changequote(,)dnl
if test "x$GCC" = "xyes"; then
  case " $CFLAGS " in
  *[\ \	]-Wall[\ \	]*) ;;
  *) CFLAGS="$CFLAGS -Wall" ;;
  esac
fi
changequote([,])dnl

#############xmorph
dnl see for details in  "info autoconf"


dnl NO it blocks the 2nd one, cannot use both
dnl AC_PATH_X

dnl Find additional X libraries, magic flags, etc.
dnl in particular, it defines the linker  definition "-L///" 
dnl as @X_LIBS@
dnl see for details in  "info autoconf"
dnl  and in  /usr/share/autoconf/acspecific.m4


if test "x$with_xmorph" != xno ; then
 AC_MSG_CHECKING([libraries needed for xmorph])
  #### PATH XTRA
  AC_PATH_XTRA
dnl the Debian extension 
dnl AC_PATH_XTRA(Xaw,X11/Xaw/MenuButton.h,'MenuButtonWidgetClass a=NULL;')
dnl does not work!
  if  test "x$have_x" = "xyes" ; then
  #### X11/Xaw/MenuButton.h
   SAVECFLAGS="$CFLAGS"
   CFLAGS="$CFLAGS $X_CFLAGS"
   AC_MSG_WARN([ "(Using CFLAGS='"$CFLAGS"' for the following test)" ])
   AC_CHECK_HEADER(X11/Xaw/MenuButton.h, [ : ]  , [ have_x=no  ] )
   CFLAGS="$SAVECFLAGS"
  #### 
  fi
fi

if  test "x$have_x" = "xyes" ; then
 if test "x$with_xmorph" = x ; then
  AC_MSG_NOTICE([ Will build xmorph. ])
  #force yes
  with_xmorph=yes
 fi
else #have_x=yes
 AC_MSG_WARN([ Either you have disabled X support, or you have specified --without-x ])
 if test "x$with_xmorph" = xyes ; then
  AC_MSG_ERROR([ May not build xmorph. ])
  exit 1
 else
  with_xmorph=no
  AC_MSG_WARN([ Will not build xmorph. ])
 fi
fi #have_x

################### morph

if ! test "x$with_morph" = xno ; then
 echo Will build  morph.
 #force default
 with_morph=yes
fi



################## gtkmorph

if test "x$with_gtkmorph" = xno ; then
 AC_MSG_NOTICE([ gtkmorph will not be compiled ])
else
 AC_MSG_CHECKING([libraries needed for gtkmorph])
 #sanity check
 test "$gtkmorph_gtk" = ""  || exit 1

echo Testing GTK $with_gtk  libraries...

if test "x$with_gtk" != "x1" -a "$gtkmorph_gtk" = ""  ; then
  pkg_modules="gtk+-2.0 >= 2.0.0"
  PKG_CHECK_MODULES(GTK, [$pkg_modules],
  gtkmorph_gtk=gtk2,
  [if test  "x$with_gtk" = "x2" ; then
   AC_ERROR([ libgtk 2 is not available ])
   exit 1
  fi;])
 else
  echo Testing for GTK 2 skipped
fi


AC_SUBST(GTK_CFLAGS)
AC_SUBST(GTK_LIBS)


if test "x$with_gtk" != "x2"  -a "$gtkmorph_gtk" = "" ; then
AM_PATH_GTK(1.2.0 , 
  gtkmorph_gtk=gtk1 ,
 [echo Cannot find GTK 1.2: Is gtk-config in path? 
  if test "x$with_gtk" = "x1" ; then
    AC_ERROR([])
  fi
 ]
)
else
  echo Testing for GTK 1.2 skipped
fi


dnl if test "x$gtkmorph_gtk" != xno ; then
dnl  if echo $GTK_LIBS | grep  libart > /dev/null  ; then
dnl  echo libart is a part of this version of gtk
dnl else
dnl  AM_PATH_LIBART(, ,
dnl   echo Cannot find libart: gtkmorph will be less functional
dnl   #gtkmorph_gtk=no
dnl  )
dnl fi
dnl else
dnl  echo libart not tested
dnl fi



if test "$gtkmorph_gtk" = gtk1  ; then
 if echo $GTK_LIBS $PACKAGE_LIBS | grep  gdk.pixbuf > /dev/null  ; then
  echo gdk-pixbuf is a part of this version of gtk
  GDK_PIXBUF_LIBS=""
  GDK_PIXBUF_FLAGS=""
 else
  dnl NO LONGER AVAILABLE HERE, SORRY : AM_PATH_GDK_PIXBUF 0.9.0, ,
   AC_MSG_ERROR([ Cannot find gdk-pixbuf: gtkmorph may not be compiled ])
   gtkmorph_gtk=''
 fi
else
  AC_MSG_NOTICE([ Testing for gdk-pixbuf skipped. ])
fi


if test "$gtkmorph_gtk" = "gtk2"  ; then
  pkg_modules="gthread-2.0"
  PKG_CHECK_MODULES(GTHREAD, [$pkg_modules]  )
 else
  AC_MSG_NOTICE([ Testing for gthreads skipped.])
fi


if test "x$gtkmorph_gtk" = x  ; then
  if test "x$with_gtkmorph" = xyes ; then
      AC_MSG_ERROR([ gtkmorph may not be compiled ])
      exit 1
   else
      AC_MSG_WARN([ Not compiling gtkmorph ])
      with_gtkmorph=no
   fi
else
  with_gtkmorph=yes
fi

fi ## of : if test "x$with_gtkmorph" = xno ; then


##################### tkmorph

if  test "x$with_tkmorph" = xyes ; then
 AC_MSG_NOTICE([Will build  tkmorph... testing needed libraries...])
 #force default
 with_tkmorph=yes

dnl Adds the following arguments to configure:
dnl                --with-tcl=...
dnl Defines the following vars:
dnl               TCL_BIN_DIR

 SC_PATH_TCLCONFIG

dnl Locate the tkConfig.sh file
dnl Defines the following vars:
dnl                TK_BIN_DIR

 SC_PATH_TKCONFIG
else
  AC_MSG_NOTICE([ Not compiling  tkmorph.])
fi #with tkmorph


#################################


dnl automake conditionals
AM_CONDITIONAL(COND_MORPH, test "x$with_morph" = xyes  )
AM_CONDITIONAL(COND_XMORPH, test "x$with_xmorph" = xyes )
AM_CONDITIONAL(COND_GTKMORPH, test "x$with_gtkmorph" = xyes )
AM_CONDITIONAL(COND_TKMORPH, test "x$with_tkmorph" = xyes )
AM_CONDITIONAL(COND_GTK2, test "x$gtkmorph_gtk" = xgtk2 )

dnl AM_CONDITIONAL(COND_LIBPLY, test "x$with_libply" != xno )
dnl AM_CONDITIONAL(COND_PLYVIEW, test "x$with_plyview" = xyes )

dnl AM_CONDITIONAL(COND_LIBPLY, false )
dnl AM_CONDITIONAL(COND_PLYVIEW, false )

dnl :ACGM: some courtesy message

if  test "x$with_morph" = xyes ; then
 AC_MSG_NOTICE([The Makefile will build morph. ])
fi

if  test "x$with_xmorph" = xyes ; then
  AC_MSG_NOTICE([The Makefile will build xmorph. ])
fi

if  test "x$with_gtkmorph" = xyes ; then
  AC_MSG_NOTICE([The Makefile will build gtkmorph. ])
fi

#if   test "x$with_plyview" = xyes ; then
#  AC_MSG_NOTICE([The Makefile will build plyview.
#fi

if  test "x$with_tkmorph" = xyes ; then
 echo The Makefile will try to build tkmorph.
 echo We are very sorry but tkmorph is not fully developed now.
 echo The project will not build properly
fi


dnl #####################


AC_OUTPUT([
po/Makefile.in
Makefile
doc/Makefile
libmorph/Makefile
morph/Makefile
xmorph/Makefile
gtkmorph/Makefile
glade1/Makefile
glade2/Makefile
tkmorph/Makefile
])

