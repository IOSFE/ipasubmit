

## 引言
在进行iOS应用上架时，有时会遇到构建版本无效的问题，即通过XCode上传成功后，但在App Store Connect的TestFlight中无法显示构建版本，或者显示一会儿后就消失了。本文将介绍可能的原因分析，并提供解决问题的方法。

## 问题描述
最近一次上传新版本至App Store后，发现在App Store Connect的TestFlight中无法显示构建版本，或者显示一会儿后就消失了。

## 原因分析
经过分析，可能的原因有两个：

1. 苹果开发者计划许可协议的更新：若长时间未登录开发者账号，在登录后可能需要同意新的许可协议。
2. 使用了permission_handler 3.0.1权限控制插件：即使在项目的ios/Runner/Info.plist文件中已经添加了权限配置代码，仍可能导致构建版本无效的问题。

## 解决问题
针对以上两个原因，我们提供以下解决方案。

### 解决方案一：同意新的许可协议

1. 登录开发者账号。
2. 检查是否出现红色提示，提示许可协议更新。如果有，请点击同意或勾选同意选项。

### 解决方案二：添加所有权限配置

1. 在ios/Runner/Info.plist文件中添加以下权限配置代码：

```xml
<key>NSAppleMusicUsageDescription</key>
<string>App需要您的同意,才能访问媒体资料库</string>
<key>NSBluetoothAlwaysUsageDescription</key>
<string>是否允许使用您的蓝牙来连接蓝牙设备？</string>
<key>NSBluetoothPeripheralUsageDescription</key>
<string>是否允许使用您的蓝牙来连接蓝牙设备？</string>
<key>NSCalendarsUsageDescription</key>
<string>是否允许此APP使用日历？</string>
<key>NSCameraUsageDescription</key>
<string>是否允许需要使用您的相机来进行拍照？</string>
<key>NSContactsUsageDescription</key>
<string>是否允许此APP访问您的通讯录？</string>
<key>NSLocationAlwaysUsageDescription</key>
<string>是否允许此APP访问您的地理位置？</string>
<key>NSLocationWhenInUseUsageDescription</key>
<string>是否允许此APP访问您的地理位置？</string>
<key>NSMicrophoneUsageDescription</key>
<string>是否允许此APP使用您的麦克风？</string>
<key>NSMotionUsageDescription</key>
<string>App需要您的同意,才能访问运动与健身</string>
<key>NSPhotoLibraryAddUsageDescription</key>
<string>App需要您的同意,才能访问相册？</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>是否允许使用您的媒体资料来选取多媒体文件？</string>
<NSSpeechRecognitionUsageDescription>
<string>是否允许此App使用语音识别？</string>
```

2. 将所有权限配置都添加到Info.plist中。

### 解决方案三：重新上传构建版本

1. 修改App的build version号码。
2. 重新进行上传操作。
3. 等待片刻，构建版本应该会显示出来。

## 知识点补充
​
补充一个小知识点，iOS上架开发者可以借助appuploader工具进行安装测试。该工具可以通过扫码的方式将APP安装到手机上，同时提供了证书制作、描述文件制作、App提交和安装测试等功能，极大地简化了iOS应用上架的步骤。
![在这里插入图片描述](https://img-blog.csdnimg.cn/direct/78f47b98191b46aa90123728bae45782.png)



## 总结
本文介绍了iOS构建版本无效的问题并提供了三种解决方案。若遇到构建版本无效的情况，可以根据上述方法尝试解决。


