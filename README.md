# XCFrameworkScripts
Useful Scripts used to build XCFramework and links to learning materials. 

# Introduction
The following scripts can be copy pasted to terminal (Make sure you are inside a project folder) and produce .framework then the final script is used to combine the individual generated archives into single .XCFramework ready for distribution. 

# Build for iOS iPhone (Release)

```shell
xcodebuild archive \
-scheme <YOUR FRAMEWORK NAME> \
-configuration Release \
-destination 'generic/platform=iOS' \
-archivePath './build/<YOUR FRAMEWORK NAME>.framework-iphoneos.xcarchive' \
SKIP_INSTALL=NO \
BUILD_LIBRARIES_FOR_DISTRIBUTION=YES

```
The above command will generate an archive of your framework by using the following list as inputs :

1. **-scheme <YOUR FRAMEWORK NAME>**: It’ll use this scheme for archiving (Make sure you specify a project name/scheme as it appear on the Xcode project).
2. **-configuration Release**: It’ll use the release configuration for building.
3. **-destination ‘generic/platform=iOS’**: This is the architecture type.
4. **-archivePath**: It saves archives into this folder path with the given name.
5. **SKIP_INSTALL**: Set NO to install the framework to the archive.
6. **BUILD_LIBRARIES_FOR_DISTRIBUTION**: Ensures your libraries are built for distribution and creates the interface file.



# Build for iOS Simulator (Release)
```shell
xcodebuild archive \
-scheme <YOUR FRAMEWORK NAME> \
-configuration Release \
-destination 'generic/platform=iOS Simulator' \
-archivePath './build/<YOUR FRAMEWORK NAME>.framework-iphonesimulator.xcarchive' \
SKIP_INSTALL=NO \
BUILD_LIBRARIES_FOR_DISTRIBUTION=YES
```
  
  These command options are the same as those for iOS except for the following differences:

1. **-destination ‘generic/platform=iOS Simulator’**: This is where you set the architecture type.
2. **-archivePath**: This generates the archive into the folder path with the given name.
   
# Build for macOS (Release)
  ```shell
  xcodebuild archive \
-scheme <YOUR FRAMEWORK NAME> \
-configuration Release \
-destination 'platform=macOS,arch=x86_64,variant=Mac Catalyst' \
-archivePath './build/<YOUR FRAMEWORK NAME>.framework-catalyst.xcarchive' \
SKIP_INSTALL=NO \
BUILD_LIBRARIES_FOR_DISTRIBUTION=YES
  ```
  
  This command is the same as the others except for the following differences:

1. **-destination ‘platform=macOS,arch=x86_64,variant=Mac Catalyst’**: This is where you indicate the architecture type.
2. **-archivePath**: This generates the archive into the folder path with the given name.


  # Generate XCFramework
  This command adds your XCFramework to the build folder using the generated archives above.
  ```shell
  xcodebuild -create-xcframework \
-framework './build/<YOUR FRAMEWORK NAME>.framework-iphonesimulator.xcarchive/Products/Library/Frameworks/<YOUR FRAMEWORK NAME>.framework' \
-framework './build/<YOUR FRAMEWORK NAME>.framework-iphoneos.xcarchive/Products/Library/Frameworks/<YOUR FRAMEWORK NAME>.framework' \
-framework './build/<YOUR FRAMEWORK NAME>.framework-catalyst.xcarchive/Products/Library/Frameworks/<YOUR FRAMEWORK NAME>.framework' \
-output './build/<YOUR FRAMEWORK NAME>.xcframework'
  ```
  
  


# Credits
1. [Raywenderlich -> Creating a Framework for iOS](https://www.raywenderlich.com/17753301-creating-a-framework-for-ios#toc-anchor-002)
2. [Official Apple Docs -> Create an XCFramework](https://help.apple.com/xcode/mac/11.4/#/dev544efab96)
  
# Other Learning Materials
- [WWDC 2019: Adopt Swift Packages in Xcode](https://developer.apple.com/wwdc19/408)

- [WWDC 2019: Binary frameworks in Swift](https://developer.apple.com/wwdc19/416)
  
- [WWDC 2019: Adopt Swift Packages in Xcode](https://developer.apple.com/wwdc19/408)


- [WWDC 2020: Distribute Binary frameworks as Swift packages](https://developer.apple.com/wwdc20/10147)

- [WWDC 2021: Swift packages collections (grouping)](https://developer.apple.com/wwdc21/10197)


- [WWDC 2020, Creating Swift packages](https://developer.apple.com/wwdc19/410)


- [WWDC 2022: Swift package plugins](https://developer.apple.com/wwdc22/110359)
