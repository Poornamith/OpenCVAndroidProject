OpenCV in Android Studio:
==============

- Download the dependencies

    - OpenCV library: https://opencv.org/releases.html (Android Pack)
    - Android NDK:    https://developer.android.com/ndk/downloads/index.html



Configure OpenCV
==============

- Create a new Project

    ex:- 
        Application Name:   OpenCVTest
        Minimum SDK:        API 15
        Activity:           Empty Activity


- Add Module

     - goto:   File -> New -> Import Module
     
     - Source Directory:   "<path>\OpenCV-android-sdk\sdk\java"
    
     - Hit Next
     
     - Hit Finish


- Build Gradle and check for errors.*

    <i>(* If you encoutered with build errors, Please refer the error list at the end of the file)</i>

- Add module dependencies

    - goto: File -> Project structure
    
    - under Modules
    
        app -> Dependencies -> Add Dependencies ( + mark on top right OR hit 'Alt + Insert) -> 3.Module Dependency
    
    - choose the existing :openCVLibraryXXX
    
    - Hit OK
    
    - Hit OK
    
- add the libraries
    
    - Set the Project View/Navigate to "Android"
    
    - Right-click on "app" -> New -> Folder -> JNI Folder
    
    - tick "Change Folder Location and edit the Foler name
    
        New Folder Location:    "src/main/jniLibs/"
        
    - Copy all the files in OpenCV download path "<path>\OpenCV-android-sdk\sdk\native\libs"
    
    - Paste on "app" in Project View/Navigate and select "...\app\src\main\jniLibs"
    
    
    
CONFIGURATION IS DONE

So Lets CODE some nifty OpenCV applcations



OpenCV Test Configuration
============== 

- Test the configuration

    - MainActivity.java
        <pre>
        public class MainActivity extends AppCompatActivity {

            //create a MainActivity TAG
            private static final String TAG="MainActivity";

            //check for configuration loopholes
            static {
                if(OpenCVLoader.initDebug()) {
                    Log.d(TAG, "OpenCV successfully loaded");
                }
                else {
                    Log.d(TAG, "OpenCV not loaded");
                }
            }

            ...
        }
        </pre>
        
- Make Project (Ctrl + F9) and check for errors.*

    <i>(* If you encoutered with build errors, Please refer the error list at the end of the file)</i>





Common Errors and Workarounds
==============

- Error:Cause: failed to find target with hash string 'android-14' ...

    - Remedy: Set the Project view to "Project"
        <pre>
        Locate <projectName>\OpenCVLibraryXXX\src\build.gradle
        change the following to the current available versions in the Android Studio that you are currently working with (check the build.gradle file in <projectPath>\app\build.gradle)

        compileSdkVersion 14
        buildToolsVersion "19.1.0"

        TO (example only. Your values should be changed correctly)

        compileSdkVersion 23
        buildToolsVersion "23.0.1"
        </pre>   

- Error:Execution failed for task ':app:compileDebugNdk'. Error: NDK integration is deprecated in the current plugin.  Consider trying the new experimental plugin.  For details, see http://tools.android.com/tech-docs/new-build-system/gradle-experimental.  Set "android.useDeprecatedNdk=true" in gradle.properties to continue using the current NDK integration.

    - Remedy: goto gradle.properties and add the following line
        <pre>
        android.useDeprecatedNdk=true
        </pre>
        
Error:Execution failed for task ':app:compileDebugNdk'.
> NDK not configured.
Download the NDK from http://developer.android.com/tools/sdk/ndk/.Then add ndk.dir=path/to/ndk in local.properties.
(On Windows, make sure you escape backslashes, e.g. C:\\ndk rather than C:\ndk)        
        
     - Remedy: goto local.properties and add the following line
        <pre>
        ndk.dir=<NDK_Path>
        </pre>
        ex: ndk.dir=C\:\\AndroidStudio\\android-ndk-r15c-windows-x86_64\\android-ndk-r15c
        
        
References
==============
https://github.com/quanhua92/NDK_OpenCV_AndroidStudio/blob/master/README.md#step-to-use-ndk-in-android-studio
https://www.youtube.com/watch?v=nv4MEliij14
        
        
