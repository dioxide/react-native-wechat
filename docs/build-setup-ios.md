# Build Setup for iOS

Add the following libraries to your "Link Binary with Libraries":

- [x] `SystemConfiguration.framework`
- [x] `CoreTelephony.framework`
- [x] `libsqlite3.0`
- [x] `libc++`
- [x] `libz`

Add "URL Schema" as your app id for "URL type" in Targets > info, See 
the following screenshot for the view on your XCode:

![Set URL Schema in XCode](https://res.wx.qq.com/open/zh_CN/htmledition/res/img/pic/app-access-guide/ios/image0042168b9.jpg)

On iOS 9, add `wechat` and `weixin` into `LSApplicationQueriesSchemes` in 
`Targets` > `info` > `Custom iOS Target Properties`. Or edit `Info.plist` 
then add:

```xml
<key>LSApplicationQueriesSchemes</key>
<array>
  <string>weixin</string>
  <string>wechat</string>
</array>
```

Then copy the following in `AppDelegate.m`:

```objc
#import "RCTLinkingManager.h"

- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url
sourceApplication:(NSString *)sourceApplication annotation:(id)annotation
{
  return [RCTLinkingManager application:application openURL:url
                            sourceApplication:sourceApplication annotation:annotation];
}
```