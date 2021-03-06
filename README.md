(c) 2020 Jouni 'Mr.Spiv' Korhonen - CMake build system for adftools.
    adftools cloned from https://github.com/prb28/adftools
    and originally forked from https://github.com/bos4711/adftools 

To build "release" binaries:
  cd adftools
  cmake ./ -DCMAKE_BUILD_TYPE=Release
  make

To build "debug" binaries:
  cd adftools
  cmake ./ -DCMAKE_BUILD_TYPE=Debug
  make


The binaries can be found from the adftools/build folder.

-- original readme --

This is adftools.

adftools is a package containing various command line utilities for
ADF-files, which is a raw dump of an Amiga disk.

The current version is v0.3 and contains the following tools:

adfcopy    - copy files from host to the ADF
adfcreate  - create an ADF
adfdelete  - delete files / dirs within an ADF
adfdump    - dump the bootblock from an ADF
adfextract - extract complete file structure from an ADF
adfinfo    - show info about an ADF
adfinstall - install a bootblock to an ADF
adflist    - list all contents of an ADF
adfmakedir - create a directory within an ADF

Some of the tools utilizes zlib and will therefore work with
compressed ADF-files (.adf.gz, .adz, ...). The tools that does not
utilize zlib does not tell you about it, so until this is implemented
you might in particular want to be cautious with the tool "adfinstall"
which will try to install a bootblock on a compressed ADF-file.

The workaround for this tool is to unpack the ADF before installing
the bootblock. Here's what happens:

    bos:~/git/adftools$ adfinfo apa.adf.gz
    apa.adf.gz
    ==========
    Label       : v
    Type        : Floppy Double Density - 880Kb
    Filesystem  : DOS0 (OFS)
    Cylinders   : 80
    Heads       : 2
    Sectors/Cyl : 11
    Blocks      : 1760 (0 - 1759)
    Blocks used : 1661
    Blocks free : 99

    All Done.
    bos:~/git/adftools$ adfinstall -i apa.adf.gz
    Installing an OS1.3-bootblock to 'apa.adf.gz': Done.
    All Done.
    Segmentation fault
    bos:~/git/adftools$ adfinfo apa.adf.gz

    gzip: apa.adf.gz: invalid compressed data--format violated
    Segmentation fault


Compiling adftools
==================

adftools requires ADFLib which is made by Laurent Clévy.
The sources are in adflib/.

____________
**Build with gradle-native on osx/windows(VC++)/linux**

To build: 
- install : Java 8
- type in a shell (dos cmd): ```./gradlew build```

All the binaries are in the build/ directory.
____________


adftools (C)2002-2015 Rikard Bosnjakovic <bos@hack.org>
