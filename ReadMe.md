OpenCV in Android Studio:
==============


- Download the dependancies

OpenCV library: https://opencv.org/releases.html (Android Pack)
Android NDK:    https://developer.android.com/ndk/downloads/index.html


- Create a new Project

ex:- 
    Application Name:   OpenCVTest
    Minimum SDK:        API 15
    Activity:           Empty Activity


- Add Module

 goto:   File-> New-> Import Module
    
 Source Directory:   <path>\OpenCV-android-sdk\sdk\java

 Hit Next
 Hit Finish


- Build Gradle and check for errors.*

    <i>(*If you encoutered with build errors, Please refer the error list at the end of the file)</i>




Common Errors and Workarounds
==============

- Error:Cause: failed to find target with hash string 'android-14' ...

    Remedy: Set the Project view to "Project"
    <pre>
            Locate <projectName>\OpenCVLibraryXXX\src\build.gradle
            change the following to the current available versions in the Android Studio that you are currently working with (check the build.gradle file in <projectPath>\app\build.gradle)

                compileSdkVersion 14
                buildToolsVersion "19.1.0"

                TO (example only. Your values should be changed correctly)

                compileSdkVersion 23
                buildToolsVersion "23.0.1"
    </pre>   

