## uni-app的条件编译

条件编译使用特殊的注释作为标记，在编译时根据不同的注释将注释里面的代码编译到不同平台.

###### 写法： 以 #ifdef  或者 #ifndef 加 %PLATFORM% 为开头，以 #endif 结尾.

* #ifdef:  if defined仅在某平台存在

* #inndef:  if not defined除了某平台均存在

* %PLATFORM%:  平台名称

  ```javascript
  仅在App平台出现的代码：
  #ifdef APP-PLUS
  需要条件编译的代码
  #endif
  
  除了H5平台，其他平台均存在的代码:
  #ifndef H5
  需要编译的代码
  #endif
  
  在H5平台或者微信小程序平台存在的代码
  #ifdef H5||MP-WEIXIN
  需条件编译的代码
  #endif
  ```

  %PLATFORM%可取值如下：

  | 值            | 平台           |
  | ------------- | -------------- |
  | APP-PLUS      | APP            |
  | APP-PLUS-NVUE | APP nvue       |
  | H5            | H5             |
  | MP-WEIXIN     | 微信小程序     |
  | MP-ALIPAY     | 支付宝小程序   |
  | MP-BAIDU      | 百度小程序     |
  | MP-TOUTIAO    | 字节跳动小程序 |
  | MP-QQ         | qq小程序       |
  | MP-360        | 360小程序      |
  | MP            | 以上所有小程序 |

   注意： 条件编译是利用注释实现的，在不同语法中写法不同，

  js使用 // 注释
  
  css使用  /* 注释 */
  
  vue/nvue模板中使用<!--注释-->;
  
  

