# Swift 5 on Pinebook - Manjaro ARM

## Overview
This is purely experimental. The Swift REPL is not working. Help is invited to get this fully functioning!

## Installation

Download the most recent release here: [https://github.com/futurejones/swift-arm64/releases](https://github.com/futurejones/swift-arm64/releases)

Extract the archive (extract it to a target folder of your choice)

`cd` into `usr/bin` within the extracted directory and run the swift binary

```bash
$ ./swift
```
You will then be met with some errors. ex:
```
/home/<you>/<extractedDir>/usr/bin/swift-driver: error while loading shared libraries: libncurses.so.6: cannot open shared object file: No such file or directory
```

Create links for the missing object files. ex:
```bash
ln -s /usr/lib/lib /usr/lib/libncursesw.so.6 libncurses.so.6
```

Create environment vars using `LD_LIBRARY_PATH`. I used a script for this:

```bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/<you>/<extractedDir>
```

Source the setup script and rerun the Swift binary. Keep linking object files until you get a message back that says "Welcome to Swift!"

**You should now be able to point the swift bin at swift files!**

## Notes

The repl is currently not working. I get the following error:

```
libpanel.so.6: version `NCURSES6_5.0.19991023' not found
```
