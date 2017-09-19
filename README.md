# cocos2d-proj-template

A stack template to quickly jumpstart cocos2d haskell development.

Currently supported platforms:

- android: full support, immediate building/debuging on new project initiation
- mac: only partial support, new project is able to build the haskell code as the library needed for the app; but the Xcode project required to link with the library is currently not included with the template

## Prerequisites

- stack: to use the template; also, building the project for certain platforms uses stack (e.g., mac)
- docker: needed for running the ghc-android image to build the app
- android sdk: an android sdk is needed to debug the app on your device. The `platform-tools` directory need to be in your `PATH` so that the tools inside can be invoked directly in the make script
- rsync: utility

## Usage

### Creating a new project

~~~
stack new <proj-name> https://raw.githubusercontent.com/lynnard/cocos2d-proj-template/master/cocos2d.hsfiles
~~~

You can also clone this repository somewhere and point stack to use the local copy of the template.

### Building for Android

~~~
export TARGET=android
make configure
make build
~~~

To debug (make sure that your android phone is connected and in debug mode first)

~~~
make debug 
~~~

### Building for Mac

~~~
export TARGET=mac
make build
~~~

At the end of the process `make` will complain about a `mv` command fail - this is because the Xcode project is not yet bundled with the template and the build script is trying to copy the built haskell library (`<proj-name>.a`) to the Xcode project.

TBC
