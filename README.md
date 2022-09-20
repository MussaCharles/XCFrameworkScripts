# XCFrameworkScripts
Useful Scripts used to build XCFramework and links to related tools. 

# Build for iOS iPhone (Release)

```swift
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




# Credits
1. [Raywenderlich -> Creating a Framework for iOS](https://www.raywenderlich.com/17753301-creating-a-framework-for-ios#toc-anchor-002)
