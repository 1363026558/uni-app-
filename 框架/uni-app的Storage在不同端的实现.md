#### uni-app的Storage在不同端的实现不同：

+ H5端为localStorage，浏览器限制5M大小，是缓存概念，可能会被清理
+ App端为原生的plus.storage,无大小限制，不是缓存，是持久化的。
+ 各个小程序端为自带的storage.api，数据存储生命周期跟小程序本身一直，即除了用户主动删除或者超过一定时间被自动清理，否则数据都一直可用
+ 微信小程序单个key允许存储的最大数据长度为1M，所有数据存储上限为10M
+ 支付宝小程序单条数据转为字符串后，字符串最大长度为200*1024，同一个支付宝用户，同一个小程序缓存上限为10M
+ 百度字节跳动小程序文档未说明大小限制
+ 除此之外，H5端还支持webspl、indexedDB、sessionStorage