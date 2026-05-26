# About the lsoda differential equation solver used by mrgsolve

The differential equation solver is a C++ translation of DLSODA from
ODEPACK. The C++ translation was created by Dilawar Singh and hosted
here <https://github.com/dilawar/libsoda-cxx/>. As we understand the
history of the code, Heng Li was also involved in early versions of the
code written in C. There was a potentially-related project hosted here
<https://github.com/sdwfrost/liblsoda/>.

## Details

The C++ translation by Dilawar Singh contains functions that appear to
be based on BLAS and LAPACK routines. These functions have been renamed
to be distinct from the respective BLAS and LAPACK function names.
References are given in the section below.

## History

The following history was recorded in the source code published by
Dilawar Singh:


    /*
    * HISTORY:
    * This is a CPP version of the LSODA library for integration into MOOSE
    somulator.
    * The original was aquired from
    * http://www.ccl.net/cca/software/SOURCES/C/kinetics2/index.shtml and modified
    by
    * Heng Li <lh3lh3@gmail.com>. Heng merged several C files into one and added a
    * simpler interface. [Available
    here](http://lh3lh3.users.sourceforge.net/download/lsoda.c)

    * The original source code came with no license or copyright
    * information. Heng Li released his modification under the MIT/X11 license. I
    * maintain the same license. I have removed quite a lot of text/comments from
    * this library. Please refer to the standard documentation.
    *
    * Contact: Dilawar Singh <dilawars@ncbs.res.in>
    */

## References

1.  LAPACK: <https://netlib.org/lapack/>

2.  BLAS: <https://netlib.org/blas/>
