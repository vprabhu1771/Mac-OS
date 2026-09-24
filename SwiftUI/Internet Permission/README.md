App Transport Security (ATS) is an Apple network security feature that enforces secure connections by requiring apps to use HTTPS instead of insecure HTTP. 
Introduced in iOS 9, ATS blocks any cleartext HTTP (`http://`) resource loads by default to prevent accidental data disclosure.

```
<key>NSAppTransportSecurity</key>
<dict>
  <!--Include to allow all connections (DANGER)-->
  <key>NSAllowsArbitraryLoads</key>
      <true/>
</dict>
```

I have solved it with adding some key in info.plist. The steps I followed are:

1. Opened my Projects info.plist file

2. Added a Key called NSAppTransportSecurity as a Dictionary.

3. Added a Subkey called NSAllowsArbitraryLoads as Boolean and set its value to YES as like following image.

![Image](1.png)

Clean the Project and Now Everything is Running fine as like before.
