# OpusKit
A repo for building opus framework for iOS.

# How to use

#### 0. Before build, you may want to build your own libopus.a

You can easily build one use [Opus-iOS](https://github.com/OpenFibers/Opus-iOS), then replaced the compiled libopus (version 1.1) in this repo, at `OpusKit/opus/opus/`. Or just use the compiled default one.  

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