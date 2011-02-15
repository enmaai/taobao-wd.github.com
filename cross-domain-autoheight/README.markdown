# 文件引用

- 文件引用：[proxy.html](https://github.com/taobao-wd/taobao-wd.github.com/blob/master/cross-domain-autoheight/proxy.html)
- 文件引用：[fathor.js](https://github.com/taobao-wd/taobao-wd.github.com/blob/master/cross-domain-autoheight/fathor.js)
- 文件引用：[cross.js](https://github.com/taobao-wd/taobao-wd.github.com/blob/master/cross-domain-autoheight/cross.js)

# 原理

- 适用场景：iframe跨域高度自适应
- 实现原理：通过子域中创建一个iframe（下图灰色iframe）指向父域的proxy.html，来实现控制父域的目的，在引用子域的时候，需要带上参数mathor_url=fathor.com，带入父域的域名

![img](http://cubee.github.com/doc/assets/images/x-domain.png)

文件列表

- `proxy.html` 放在父域跟下，比如fathor.com/proxy.html
- `cross.js` 跨域js，由子域的iframe中引用
- `fathor.js` 父域js，由父域的页面中引用

使用方法

父域引用子域的iframe时候，需要带上mathor_url=‘父域域名’（不带"http://"） 

	<iframe src="sub_domain.com?mathor_url=main_domain.com"></iframe>

在父域页面中引入fathor.js

	<script src="fathor.js"></script>

在子域iframe页面中引入cross.js

	<script src="cross.js"></script>
