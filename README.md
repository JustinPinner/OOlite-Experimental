OOlite-Experimental
===================

This is NOT the version of OOlite you're looking for so don't download it from here. Instead go to the official site at http://oolite.org/ and follow the download link.

FAQ
===
Q: This isn't an official OOlite repo - what are you up to?
A: I want to find out how a game is designed, and whether or not I'm smart enough to have a go at changing or extending it myself.

Q: Can I use what's in here?
A: I guess. As far as I know the source is all freely available. I'm not claiming any rights over this stuff - all IP still belongs to the original authors - check the official website at http://oolite.org/ for more info. The safest option if you do clone from here is to make sure you maintain all the README and other attribution files.

Q: Why did you create this repo?
A: I want to mess about with the OOlite code, and be able to get back to a working state when I inevitably screw it up.


Notes for building on Ubuntu.
(this isn't fully working yet but here's what I had to do to at least get the majority of the files to compile)

thanks to @mart_brooks for the tips

$ sudo apt-get install gnustep-core-devel gnustep-devel
$ sudo apt-get install libsdl1.2-dev
$ sudo apt-get install libnspr4-dev libnspr4
$ sudo apt-get install libmozjs185-dev
$ sudo apt-get install libsdl-mixer1.2-dev
$ sudo apt-get install  libespeak-dev

$ cd path/to/oolite/trunk
$ . `locate GNUstep.sh`
$ make

which seems to go along nicely and then;

 Linking objc_program oolite ...
/usr/bin/ld: cannot find -ljs_static
collect2: ld returned 1 exit status
make[3]: *** [obj.spk/oolite] Error 1
make[2]: *** [internal-objc_program-all_] Error 2
make[1]: *** [oolite.all.objc-program.variables] Error 2
make: *** [internal-all] Error 2


so I figured I'd try;

$ make -f libjs.make

but that's not quite working

Updating Javascript sources...

cd deps/Cocoa-deps/scripts && ./update-mozilla.sh
libjs is up to date.
mkdir -p deps/Cross-platform-deps/mozilla/js/src/build-release

Configuring Javascript library...

cd deps/Cross-platform-deps/mozilla/js/src/build-release && ../configure --disable-shared-js --enable-threadsafe --with-system-nspr --disable-tests --enable-trace-jscalls
loading cache ./config.cache
configure: error: can not find install-sh or install.sh in ../build/autoconf ../../build/autoconf
make: *** [deps/Cross-platform-deps/mozilla/js/src/build-release/config_stamp] Error 1


