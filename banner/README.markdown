# 对联广告

- [Demo](http://taobao-wd.github.com/banner/demo/demo.html)

# Doc

种子的引入

	YUI({
		modules:{
			
			'banner':{
				fullpath:'../banner.js',
				requires:['anim','node']
			}
		}
	}).use('banner',function(Y){
		//your code
	});

新建一个Y.Banner对象

	new Y.Banner({
		width:90,
		height:200,
		imgs:[
			{
				img:'1.jpg',
				href:''
			},
			{
				img:'2.jpg',
				href:''
			}
		],
		span:950,
		scroll:true
	});

Y.Banner 构造器

使用：	

	new Y.Banner(config);

配置：	

-	width:{Number} 广告宽度，默认为300
-	height:{number} 广告高度，默认300
-	span:{number} 对联中间的跨度，默认300
-	scroll:{boolean} 是否随着页面上下滚动，默认为true
-	anim:{boolean} 滚动过程是否为动画显示，默认为true
-	top:{number} 对联距头部高度，默认100
-	spread:{boolean} 页面宽度太窄时，广告是否往中间挤压，默认为false
-	text:{string} 关闭的文案，默认为'x'
-	closeable:{boolean} 是否显示关闭按钮，默认为true
-	autoHide:{boolean} 浏览器宽度不够时是否自动隐藏，默认为true

方法：	

- hide:隐藏广告

