YUI3 延时加载 Demo
==============

- [Demo](http://taobao-wd.github.com/yui3-lazyload/demo.html)

模仿`KISSY`的延时加载功能，包含图片延时加载和`Dom`的延时渲染（待渲染的`Dom`节点的`outerHTML`放在`textarea`中），其中图片的延时加载使用 YUI3 的 [imageloader](http://developer.yahoo.com/yui/3/imageloader/) 实现，Dom 的延时渲染只模拟了 textarea 区域滚动到可视区域后加载。在 Tab 中的隐藏延时加载未实现

YUI3 imageloader 同样实现了其他Dom事件的触发加载和自定义事件触发加载，[YUI3-imageloader](http://developer.yahoo.com/yui/3/imageloader/)

图片的延时加载
==============

需要延时加载的图片增加属性`yui-lazyload`，填入图片地址，`src`字段留空

	<img yui-lazyload="http://cdn/pic_name.jpg" />

js中通过`new Y.ImgLoadGroup`初始化，另外需要对抓取到的img标签作遍历，每个标签都通过YUI的方式注册延时加载实例。

	Y.all('img').each(function(node){ 
		if(node.getAttribute('yui-lazyload') == '')return;
		if(node.get('id') == ''){ //注册imageloader需要id
			node.set('id',Y.stamp(node));
		}
		imageloader.registerImage({ domId:node.get('id'),srcUrl: node.getAttribute('yui-lazyload') });
	});

Dom 的延时渲染
==============

将需要延时渲染的Dom节点的文本放在`textarea`中，指定`className`，命名无讲究，只为可以抓的到

	<textarea class="yui-lazyrender">
		content...
	</textarea>

js中通过在textarea之前创建一个空`div`，鉴定`window`的`onscrll`和`resize`事件，当`div`滚动到可视区域后就渲染内容，并删除监听
