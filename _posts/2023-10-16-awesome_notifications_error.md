---
title: "flutter awesome notifications no such module '__ObjC'"
date: "2023-10-16 11:43:23"
tags: ["flutter", "awesome notifications"]
---

# flutter awesome notifications - Using bridging headers with module interfaces is unsupported
```
Swift Compiler Error (Xcode): Using bridging headers with module interfaces is unsupported

Uncategorized (Xcode): Command SwiftDriver emitted errors but did not return a nonzero exit code to indicate failure

Error (Xcode): no such module '__ObjC'
/Users/Library/Developer/Xcode/DerivedData/Runner-cldosndpmrfalccuqvhqtphxsgfd/Build/Intermediates.noindex/Runner.build/Debug-iphonesimulator/Runner.build/Objects-normal/arm64/Runner.private.swiftinterface:9:18
Runner.private.swiftinterface:9

Error (Xcode): failed to verify module interface of 'Runner' due to the errors above; the textual interface may be broken by project issues or a compiler bug
/Users/Library/Developer/Xcode/DerivedData/Runner-cldosndpmrfalccuqvhqtphxsgfd/Build/Intermediates.noindex/Runner.build/Debug-iphonesimulator/Runner.build/Objects-normal/arm64/Runner.private.swiftinterface:0:0

Could not build the application for the simulator.
Error launching application on iPhone SE (3rd generation).

Exited (1).
```

### To use Awesome Notifications and build your app correctly, you need to ensure to set some build settings options for your app targets. In your project view, click on Runner -> Target Runner -> Build settings...
... and set the following options:

In Runner Target:
<br>
- Build libraries for distribution => NO
<br>
- Only safe API extensions => NO
<br>
- iOS Deployment Target => 11 or greater
<br>

In all other Targets:
<br>

- Build libraries for distribution => NO
<br>
- Only safe API extensions => YES
<br>
- iOS Deployment Target => 11 or greater
<br>

### Xcode -> Open ios/Runner.xcodeproj -> Runner -> Build Settings -> All

![Alt text](</assets/2023-10-16_ 12.15.10.png>)
<br>
<br>

### search "Standard Libra...." -> "Yes"

![Alt text](/assets/2023-10-16_12.13.59.png)
<br>
<br>

### search "Distri....." -> "No"

![Alt text](/assets/2023-10-16_12.14.32.png)
<br>
<br>

### Basic 
- Always Embed Swift Standard Libraries (Yes)
<br>
- Build Libraries for Distribution (No)
<br>
- Enable Bitcode (No)
<br>

![Alt text](/assets/2023-10-16_12.15.00.png)
<br>