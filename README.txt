README file for JBDiff (Java Binary Diff) 
Version: 0.1.1
Release date: 1 Oct 2007

JBDiff (Java Binary Diff) utility is a Java translation of the bsdiff (v4.2) utility 
by Colin Percival. See http://www.daemonology.net/bsdiff/

The file format is similar to, but currently not compatible with the bsdiff utility. 
This is because bsdiff uses bzip2 for compression which is not available in the 
standard Java libraries. Instead I use gzip (java.util.zip.*)

The diff utility is very memory hungry. Attempting to diff very large files with 
insufficient RAM may cause your computer to 'trash' (ie become unusably slow and may
require a reset to recover). Comparing two 20MB files will take approx 80 seconds 
on a 2GHz Pentium 4 and will require a maximum heap size of at least 220 MBytes. The
maximum heap size can be specified using the -Xmx switch to the Java VM (see examples
below). The patch utility has more modest resource requirements.

EXAMPLES:

To compare old.bin with new.bin and produce diff file new-old.diff:

java -Xmx200m -classpath jbdiff.jar ie.wombat.jbdiff.JBDiff old.bin new.bin new-old.diff

To patch old.bin with new-old.diff to produce new.bin:

java -Xmx200m -classpath jbdiff.jar ie.wombat.jbdiff.JBPatch old.bin new.bin new-old.diff

TODO:

This first release is a rather blind port of the bsdiff utility. A vast bulk of
the code ported to Java without any modification. There is scope 
for optimization (the C bsdiff runs in approx 50% faster than JBDiff).

Also it would be nice to be able to produce output that is compatible with bsdiff.
I need a bzip2 library for that.

Any suggestions, feedback and bugs will be much appreciated. Please email
to joe@galway.net

LICENSE:

Now available under BSD license (previously GPL).

CHANGES SINCE 0.1.0 RELEASE:

Change of license from GPL v2 to BSD license.

Joe Desbonnet
jdesbonnet@gmail.com
1 Oct 2007
