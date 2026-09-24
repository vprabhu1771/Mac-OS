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
