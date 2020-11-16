**MonoDevelop** is a full-featured integrated development environment (IDE) for mono using Gtk#.

See http://www.monodevelop.com for more info.

[![Build Status](http://jenkins.mono-project.com/job/test-monodevelop-mainline/badge/icon)](http://jenkins.mono-project.com/job/test-monodevelop-mainline/)

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/mono/monodevelop?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Directory organization
----------------------

There are two main directories:

 * `main`: The core MonoDevelop assemblies and add-ins (all in a single
    tarball/package).
 * `extras`: Additional add-ins (each add-in has its own
    tarball/package).

Compiling
---------

If you are building from Git, make sure that you initialize the submodules
that are part of this repository by executing:
`git submodule update --init --recursive`

If you are running a parallel mono installation, make sure to run all the following steps
while having sourced your mono installation script. (source path/to/my-environment-script)
See: http://www.mono-project.com/Parallel_Mono_Environments

To compile execute:
`./configure --profile=gnome; make`

Disclaimer: Please be aware that the 'extras/JavaBinding' and 'extras/ValaBinding' packages do not currently work. When prompted or by manually selecting them during the './configure --select' step, make sure they stay deselected. (deselected by default)

Running
-------

You can run MonoDevelop from the build directory by executing:
`make run`

Debugging
---------

You can debug MonoDevelop using MonoDevelop (on Linux) with the `main/Main.sln` solution. 
Use the `DebugGnome` configuration on Linux.

Installing *(Optional)*
----------

You can install MonoDevelop by running:
`make install`

Bear in mind that if you are installing under a custom prefix, you may need to modify your `/etc/ld.so.conf` or `LD_LIBRARY_PATH` to ensure that any required native libraries are found correctly.

*(It's possible that you need to install for your locale to be
correctly set.)*

Dependencies
------------

- [Unix](http://www.monodevelop.com/developers/building-monodevelop/#linux)

Special Environment Variables
-----------------------------

**BUILD_REVISION**

	If this environment variable exists we assume we are compiling inside wrench.
	We use this to enable raygun only for 'release' builds and not for normal
	developer builds compiled on a dev machine with 'make && make run'.


Known Problems
-----------------------------

```
"The type `GLib.IIcon' is defined in an assembly that is not referenced"
```

This happens when you accidentally installed gtk-sharp3 instead of the 2.12.x branch version.
Make sure to 'make uninstall' or otherwise remove the gtk-sharp3 version and install the older one.

xbuild may still cache a reference to assemblies that you may have accidentally installed into your mono installation,
like the gtk-sharp3 as described before. You can delete the cache in $HOME/.config/xbuild/pkgconfig-cache-2.xml



References
----------

**[MonoDevelop website](http://www.monodevelop.com)**

**[Gnome Human Interface Guidelines (HIG)](https://developer.gnome.org/hig/stable/)**

**[freedesktop.org standards](http://freedesktop.org/Standards/)**

Discussion, Bugs, Patches
-------------------------

https://github.com/dotdevelop/community *(questions and discussion)*

https://github.com/dotdevelop/dotdevelop/issues

