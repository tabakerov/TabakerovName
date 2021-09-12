# How to run an app that macOS doesn't allow

*Sep 12, 2021*

If you're using macOS and have an app you downloaded from internet, and you see this message:

**“dotnet-sdk-6.0.100-rc.1.21460.8-osx-x64.pkg” cannot be opened because it is from an unidentified developer.**

**macOS cannot verify that this app is free from malware.**

And if you need to run it anyway, you need to remove `com.apple.quarantine` from the file:

`xattr -d com.apple.quarantine dotnet-sdk-6.0.100-rc.1.21460.8-osx-x64.pkg`