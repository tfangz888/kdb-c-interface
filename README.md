# Interfacing KDB+ with C

The PDF documentation for this resource can be found [here][gitpdfdoc] and also on the [AquaQ Analytics][aquaqresources]
website.

Installation & Setup
--------------------

This project uses CMake 2.6+ to build across multiple platforms. It has been tested on Linux,
Windows and Mac OSX. Execute the following commands on all platforms to create platform
appropriate build files within the `build` directory.

    mkdir build; cd build; cmake ..

On Linux and Mac OSX platforms, you just need to run make install to complete the build process
and find the binary output in the `bin` directory.

        make install

On Windows platforms you will need to have the msbuild.exe available on your path. CMake creates
two Visual Studio projects that need to be built. The `INSTALL` project will not modify any of the
code and will just move the binaries from the `build` directory to the `bin` directory.

    msbuild ./ALL_BUILD.vcxproj /p:Configuration=Release
    msbuild ./INSTALL.vcxproj /p:Configuration=Release

The resulting directory after running a build should look like this:

    bin/                    -- contains the library and makeprint.q
    build/                  -- contains the makefile/visual studio projects
    src/                    -- contains the source code
    CMakeLists.txt

Running the Examples
--------------------

Once the build is complete, navigate to the `bin` directory and execute:

    q makeprint.q

This will load the C shared object and bind the functions to names (*make* and *print*). Instructions
and example commands should be displayed as soon as the the makeprint.q script loads.

    q) print[1b]
    1b
    q) print[`a`b`c!1 2 3]
    a   | 1
    b   | 2
    c   | 3

Other Resources
---------------

This resource is intended to suppliment the existing Kx Wiki sections:

* [Interfacing With C][kxwikiinterface]
* [Extending With C][kxwikiextend]

[aquaqwebsite]: http://www.aquaq.co.uk  "AquaQ Analytics Website"
[aquaqresources]: http://www.aquaq.co.uk/resources "AquaQ Analytics Website Resources"
[gitpdfdoc]: https://github.com/markrooney/kdb-c-interface/blob/master/docs/InterfacingWithC.pdf
[kxwikiinterface]: http://code.kx.com/wiki/Cookbook/InterfacingWithC "Kx Wiki Interfacing with C"
[kxwikiextend]: http://code.kx.com/wiki/Cookbook/ExtendingWithC "Kx Wiki Extending with C"