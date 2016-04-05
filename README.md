# OpusKit
A repo for building opus framework for iOS.

#### Before build, you may want to build your own libopus.a

You can easily build one use [Opus-iOS](https://github.com/OpenFibers/Opus-iOS), then replaced the compiled libopus (version 1.1.2) in this repo. For framwork, replace it at `Build for framework/OpusKit/opus/opus/`; for static lib, at `Build for static lib/OpusKit/opus/include/*.h` and `Build for static lib/OpusKit/opus/opus/lib/libopus.a`.   

Or just use the compiled default one.  

# Build for framework

#### 1. Open Xcode, build for simulator, using release build configuration.  
#### 2. Build for device, using release build configuration.  
#### 3. Run this script from "Products" folder:

```
➜  lipo -create -output "OpusKit" "Release-iphoneos/OpusKit.framework/OpusKit" "Release-iphonesimulator/OpusKit.framework/OpusKit" 
```

#### 4. Check the archs contained by binary file

```
➜  lipo -info OpusKit 
Architectures in the fat file: OpusKit are: i386 x86_64 armv7 armv7s arm64 
```
A normal OpusKit file comes with this five archs: i386, x86_64, armv7, armv7s, arm64.

#### 5. Recreate a framework for all archs

```
➜  cp -R Release-iphoneos/OpusKit.framework ./OpusKit.framework
➜  mv OpusKit ./OpusKit.framework/OpusKit
```

#### 6. Add OpusKit to your project

Just drag OpusKit.framework into your project, then in the project's 'General' tab, add OpusKit.framework to 'Embedded Binaries'

# Build for static lib

#### 1. Open Xcode, build for simulator, using release build configuration.  
#### 2. Build for device, using release build configuration.  
#### 3. Run this script from "Products" folder:

```
➜  lipo -create -output "libOpusKit.a" "Release-iphoneos/libOpusKit.a" "Release-iphonesimulator/libOpusKit.a" 
```

#### 4. Check the archs contained by binary file

```
➜  lipo -info libOpusKit.a 
Architectures in the fat file: libOpusKit.a are: i386 x86_64 armv7 armv7s arm64 
```
A normal OpusKit file comes with this five archs: i386, x86_64, armv7, armv7s, arm64.

#### 5. Copy headers and libOpusKit.a to your project

Just copy all headers in OpusKit/opus/include and merged libOpusKit.a to your project.
