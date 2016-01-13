# OpusKit
A repo for building opus framework for iOS.

# How to use

#### 1. Build for simulator, using release build configuration.  
#### 2. Build for device, using release build configuration.  
#### 3. Run this script from "Products" folder:

```
➜  lipo -create -output "OpusKit" "Release-iphoneos/OpusKit.framework/OpusKit" "Release-iphonesimulator/OpusKit.framework/OpusKit" 
```

#### 4. Check the archs contained by binary file

```
➜  Products  lipo -info OpusKit 
Architectures in the fat file: OpusKit are: i386 x86_64 armv7 armv7s arm64 
```

#### 5. Recreate a framework for all archs

```
➜  cp -R Release-iphoneos/OpusKit.framework ./OpusKit.framework
➜  mv OpusKit ./OpusKit.framework/OpusKit
```