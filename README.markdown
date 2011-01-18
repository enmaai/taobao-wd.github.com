# 关于Taobao WD Gallery

`Taobao WD Gallery` 是淘宝北京 FE 团队 Demo 预览的沉淀和积累，是 [guide 手册](https://github.com/taobao-wd/guide)的兄弟项目，由团队成员贡献代码和维护文档，成员开通编辑权限请联系`拔赤`。

每个 Demo 占用一个目录，Demo 目录中必须配备 README，Demo 需要做到良好的浏览器兼容，全局库(`YUI3`/`cssreset`/`cssgrid`)的引用直接使用cdn地址，使用图片尽可能传至 tps 中，Markdown 语法格式请参照[这里](http://daringfireball.net/projects/markdown/syntax)。淘宝北京前端团队选用 [YUI3](http://developer.yahoo.com/yui/3/) 作为基础库。

	http://a.tbcdn.cn/yui/2.8.0r4/build/yuiloader/yuiloader-min.js
	http://a.tbcdn.cn/yui/3.0.0/build/yui/yui-min.js
	http://a.tbcdn.cn/yui/3.1.0/build/yui/yui-min.js
	http://a.tbcdn.cn/s/yui/3.2.0/build/yui/yui-min.js
	http://a.tbcdn.cn/s/yui/3.3.0/build/yui/yui-min.js

Taobao WD Gallery 的整理离不开 [Cubee 项目](http://cubee.github.com/doc/),`Cubee`项目的维护已经暂停

# Css Reset & Css Grid

## Css Reset 

Css Reset 使用 Kissy-Reset

- [Kissy CssReset Doc](http://docs.kissyui.com/kissy/docs/cssreset/index.html)
- [英文测试页](http://kissyteam.github.com/kissy/src/cssreset/test.html)
- [中文测试页](http://kissyteam.github.com/kissy/src/cssreset/test-post.html)

css reset 引用地址：

	http://a.tbcdn.cn/s/kissy/1.1.6/cssreset/reset-min.css

## Css Grid 

使用 Kissy 中的 950 栅格系统,990栅格和950栅格本质上无异，只需重新定义全局容器的宽度为990即可

- [Kissy CssGrid Doc](http://docs.kissyui.com/kissy/docs/cssgrids/index.html)
- [Demo 页面](http://kissyteam.github.com/kissy/src/cssgrids/grids-taobao.html)
- [布局尺寸实例](http://docs.kissyui.com/kissy/src/cssgrids/grids-taobao.css) - 项目中需要自行解决布局尺寸，可参照 Demo 和 [实例代码](https://gist.github.com/784105)
- [命名规则和样式生成工具](http://kissyteam.github.com/kissy/src/cssgrids/css-generator.html)

css grid 引用地址：

	http://a.tbcdn.cn/s/kissy/1.1.6/cssgrids/grids-min.css

如果自己实现栅格，可以参考 [Cubee Grid Demo](http://cubee.github.com/src/css/demo/grid.html)，栅格布局原理可以参照 [Cubee Grid Doc](http://cubee.github.com/doc/start.html#cssgrid)，以及[栅格实现原理ppt](http://www.slideshare.net/lijing00333/ss-5023289)

`base.css`包含`reset.css`和`grid.css`,引用地址:

	http://a.tbcdn.cn/s/kissy/1.1.6/cssbase/base.css

# Examples

## 基于YUI3的延时加载
- [Lazyload Doc](https://github.com/taobao-wd/taobao-wd.github.com/blob/master/yui3-lazyload/README.markdown)
- Demo:[yui3-lazyload.html](http://taobao-wd.github.com/yui3-lazyload/demo.html)

## html5-templete
- [html5-templete Doc](https://github.com/taobao-wd/taobao-wd.github.com/blob/master/html5-templete/README.markdown)
- Demo:[html5.html](http://taobao-wd.github.com/html5-templete/html5.html)
- Demo:[html5-reset.css](http://taobao-wd.github.com/html5-templete/html5-reset.css)
- Demo:[html5.js](http://taobao-wd.github.com/html5-templete/html5.js)

# Widgets

