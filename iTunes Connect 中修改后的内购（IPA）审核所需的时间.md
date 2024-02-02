
## 引言

在 iOS 开发过程中，将应用上传到 App Store 是一个重要的步骤。应用审核和 IAP 商品审核是分开的，审核一般需要等待一周左右。如果审核通过，我们会收到 Apple 发来的反馈邮件，根据邮件中的指示进行后续操作。如果已经上架的应用需要添加 IAP 商品或者修改 IAP 价格等，直接提交 IAP 审核即可，不需要再次提交应用审核。提交应用审核可以使用 [AppUploade](https://www.kxapp.com/)r 工具，非常简单方便，下面具体来讲讲吧。
![在这里插入图片描述](https://img-blog.csdnimg.cn/direct/f42f1213189d4b5cafd4de4f07c9a306.png)


## 摘要

本文将介绍使用 [AppUploader](https://www.kxapp.com/) 工具提交上传 iOS 应用和 IAP 商品的步骤，包括选择 IPA 文件和通道、设置专用密码、提交上传并审核等。通过本文的指导，开发者可以轻松完成应用和 IAP 商品的上传和审核过程。

## 正文

### 一、选择 IPA 文件和通道

首先，在提交上传界面中，我们需要选择相应的 IPA 文件。这个文件是经过开发者编译生成的应用程序包，其中包含了应用的代码、资源和配置信息。

在提交界面的右上角，有四个通道可供选择：1，2，3 和老通道。根据实际情况，选择合适的通道进行上传。

### 二、设置专用密码

为了保证上传的安全性，我们需要设置专用密码。这个密码将用于验证用户身份，确保只有授权的人员能够进行上传操作。

![在这里插入图片描述](https://img-blog.csdnimg.cn/direct/4dba98fc0b854c3f981cda5b617e6870.png)


### 三、上传 IPA 文件

在选择 IPA 文件和设置密码后，我们可以开始进行上传操作。点击上传按钮，等待上传完成。


![在这里插入图片描述](https://img-blog.csdnimg.cn/direct/354ae583ef1c4a148000d7d2c98f6c14.png)

### 四、添加 IAP 商品

如果需要添加 IAP 商品，可以通过 iTunes Connect 界面进行添加。添加完成后，我们需要使用 AppUploader 工具来提交审核。

```swift
let inAppPurchase = InAppPurchase()
inAppPurchase.productID = "com.example.product1"
inAppPurchase.type = .consumable
inAppPurchase.referenceName = "Product 1"
inAppPurchase.price = 0.99

let submitResult = uploader.submitInAppPurchase(inAppPurchase)

// 检查提交结果
if submitResult.successful {
    print("IAP 商品提交成功！")
} else {
    print("IAP 商品提交失败：\(submitResult.error)")
}
```

### 五、审核过程

上传和提交审核完成后，我们需要等待 Apple 的审核结果。一般情况下，审核时间为一周左右。审核完成后，我们会收到 Apple 发来的反馈邮件，根据邮件中的指示进行后续操作。

需要注意的是，在审核过程中可能会出现各种问题，比如证书过期、网络连接问题等，开发者需要及时处理这些问题，并重新提交审核。

### 六、注意事项

在使用 AppUploader 工具进行上传和审核时，需要注意以下几个方面：

1. 确认开发者账号是否已经支付了相应的费用，才能使用该工具进行上传和审核。

2. 在选择 IPA 文件前，需要将应用编译生成 IPA 文件，并确保文件路径准确无误。

3. 在设置专用密码时，需要确保密码的安全性，不要轻易泄露。

4. 上传和审核过程中可能会出现各种问题，开发者需要及时处理这些问题，并重新提交上传和审核。

### 七、总结

本文介绍了使用 AppUploader 工具上传 iOS 应用和 IAP 商品的步骤和注意事项，同时提供了相应的代码示例。通过本文的指导，开发者可以轻松完成应用和 IAP 商品的上传和审核过程，并确保上传和审核的安全性和有效性。

## 参考资料

- [AppUploader](https://www.kxapp.com/)
- [上传 iOS 应用到 App Store](https://www.applicationloader.net/doc/hot/uploader.html)
- [iTunes Connect 中 IAP 商品的添加和审核](https://www.applicationloader.net/doc/hot/uploader.html)
