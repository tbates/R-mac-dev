# TODO 
[ ] Remove call to wipe a/b
[ ] Build and return a dataframe
[ ] Switch from cat to printing a kable
[ ] Store results in a database/spreadsheet file
[ ] Function or how-to to allow user to switch blas

1. Open terminal.app and cd to where the relevant files are to keep commands manageable in length

cd /Library/Frameworks/R.framework/Resources/lib/

2. Find the paths to different versions of veclib by  ls’ing the directory they should live in:

ls -l libRblas*dylib

The existing symbolic link will look like this

lrwxr-xr-x  1 root  admin      16 24 Sep 12:10 libRblas.dylib -> libRblas.0.dylib


Which means calls to “libRblas.dylib” will resolve to "libRblas.0.dylib"

3. Overwrite this link with a new one from Apple's veclib (libRblas.vecLib.dylib ) to libRblas.dylib

ln -s -i -v libRblas.vecLib.dylib libRblas.dylib


When you restart R, it should now call libRblas.vecLib.dylib for math

To switch back

cd /Library/Frameworks/R.framework/Resources/lib/
ln -s -i -v libRblas.0.dylib libRblas.dylib

