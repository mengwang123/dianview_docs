# iOS 开发者常见问题

#### 如何获取包名？（请注意，包名填写后不可修改，请谨慎填写！）

> 1、从工程中获取![img](img/sdk_lookbundleID.png)
> 2、从ipa包中获取，解压缩ipa包，找到info.plist文件，其中的Bundle identifier就是包名。

#### “应用市场id”是什么?

> 对iOS来说就是itunes id，比如一个应用在app store上的链接是 `https://itunes.apple.com/cn/app/you-buuber-chu-xing-shou-xuan/id368677368?mt=8`, id就是368677368

#### SDK支持的iOS系统版本是多少？

> 7.0以上都可以用

#### 我的应用还没有上架怎么办？

> 如果应用已在架上只是还没有嵌入SDK，在创建应用时，可以直接填入app store链接或ID，此链接的作用是方便我们获取一些应用的固有属性。

> 如应用从未上架过，在创建应用时，请点击右下方的链接 `应用还没有上架？请点击`。应用正式上架之后，可再在“应用列表”页面中编辑应用属性，填入app store链接或ID。