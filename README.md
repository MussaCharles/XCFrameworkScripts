# XCFrameworkScripts
Useful Scripts used to build XCFramework and links to related tools. 

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




# Credits
1. [Raywenderlich -> Creating a Framework for iOS](https://www.raywenderlich.com/17753301-creating-a-framework-for-ios#toc-anchor-002)
