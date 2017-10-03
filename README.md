# opengl-headers

Wrap of Khrono's headers into a nice CMake-installable package

This package is released under the MIT license (or "Expat license", as stated
by FSF).

## Why?

You need a header with OpenGL definitions to be able to write an OpenGL
application. That's a "duh" if you know C/C++. Usually, one gets it from the
operating system (ex: the OpenGL framework on Mac). But those headers are
distributed from Khronos under the Expat/MIT license, which means you can embed
it inside another package with compatible license (ex: MIT or GPL).

Therefore, this MIT-licensed package conveniently allows you to deploy a truly
multiplatform header, avoiding #ifdefs. And CMake also allows you to embed it
using many different ways.

## The headers

The creation of this package is as simple as it can be. It's the "api" folder
from Khronos repo: https://github.com/KhronosGroup/OpenGL-Registry

It's manually copied because Khrono's repository is rather large (~260mb on
disk).

## How to use this library

You have two main options. You can install it, then #import it directy, or use
CMake's "findpackage", or add it as a "git submodule" and use CMake's
"add_subdirectory".

