# Building libARvideo Using QuickTime
 
## What is the relationship between libARvideo and QuickTime?

QuickTime is Apple's media-handling library, available on both Mac OS X and the Windows platforms. From the point of view of ARToolKit Professional, QuickTime provides a standardized way of accessing video capture hardware on Mac OS X and Windows. This allows ARToolKit Professional to acquire video from a large range of USB webcams and other video capture hardware, as well as read pre-recorded video from files on disk or via network streaming.

## Why do I need to know about QuickTime?

While the QuickTime libraries and SDK are in every release of Mac OS X, and can be used right away, they are not installed by default on Windows. Every user who wants to run an ARToolKit application that uses QuickTime for video capture on Windows will need to install QuickTime. This is not onerous - any user who already has iTunes for Windows installed will have QuickTime installed already. Other users should visit the [QuickTime for Windows download page][1].

Additionally, for customers using Windows who do wish to recompile libARvideo for their own purposes, the QuickTime SDK must be downloaded and installed.

## How to install the QuickTime SDK

**Mac OS X:** The QuickTime SDK is installed by default along with XCode, and no further action should be needed.

**Windows:** [Download the QuickTime SDK for Windows][2].

We recommend installing the SDK to the default location, C:\\Program Files\\QuickTime SDK. This is because the paths in ARToolKit Professional's build files expect this location.

### Setting up Microsoft Visual Studio to use the QuickTime SDK

ARToolKit Professional's build files expect to find QuickTime at C:\\Program Files\\QuickTime SDK. Unless you change this location, no further setup is required.

## How to recompile libARvideo under Microsoft Visual Studio

libARvideo will only include the QuickTime video interface if the constant AR_INPUT_QUICKTIME is defined in <AR/config.h>. This is **NOT** the default, so you should open config.h, locate the constant and change the \#undef in front of it to \#define.

The QuickTime module can be selected at runtime by passing -device=QUICKTIME in the video config string (the parameter to arVideoOpen()). If you also wish to have the QuickTime module used by default, locate the constant AR_DEFAULT_INPUT_QUICKTIME and change the \#undef in front of it to \#define.

From there, compiling should be just a matter of right-clicking on "ARVideo" in the solution explorer and choosing "Build."

If you are having difficulty with these instructions, please post a message on the [forum][3]) or contact an ARToolworks support person.

[1]: http://www.apple.com/quicktime/download/       "Download QuickTime For Windows"
[2]: http://developer.apple.com/quicktime/download/ "Download QuickTime SDK For Windows"
[3]: http://www.artoolworks.com/support/forum       "ARToolworks Forum"