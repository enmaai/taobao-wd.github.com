# Postip

- [Demo](http://taobao-wd.github.com/postip/demo/index.html)

# Doc

-	可以通过扩展Y.Postip来实现自定义相对提示层
-	相对提示层是相对于触发层的25个固定定位和相对于触发层top、left的自定义数值,如下图
	
![img](http://cubee.github.com/src/postip/demo/img/aligntemp.png)

-	相对提示层的默认z-index为1000，可以设置触发层的z-index级别来得到想要的效果，如例中第三种方式。
-	每新建一个Y.Postip对象会生成一个相对提示层，放出相对提示层的样式可设置，丰富表现
-	IE6下设置了iframe遮盖Select
-	相对提示层的内容可设置text或html，同样也可以指定相对提示层为已存在Dom对象，如例中第四种方式。
-	新建内容如果为空将会从触发层的 rel 中取值。如例中第二第三种方式。
-	目前在ie下发现对get('region')的值解释有bug，导致相对提示层有偏移，试验过可以通过对触发层的csshack得到对其

种子的引入

	modules:{
		'postip':{
			fullpath:'../postip.js',
			requires:['node']
		}
	}

新建一个Y.Postip对象
	var Demo = new Y.Postip('demo1',{pos:{h:'30',v:'-30'},content:'<div class="sb"><p>Tips<a href="#">Close</a></p></div>',eventype:'click'});

使用：	

	new Y.Postip(options);

配置：		

-	pos.h:{string} 相对提示的水平对齐方式，默认 left，{oleft,left,center,right,oright,正负数值可选}
-	pos.v:{string} 相对提示的垂直对齐方式，默认 top，{otop,top,middle,bottom,obottom,正负数值可选}
-	eventype:{string} 触发相对提示层的鼠标事件，默认为mouseover，可选click
-	mouseout:{boolean} 鼠标离开相对弹出层或触发层时，相对弹出层是否消失，默认true
-	classname:{string} 相对弹出层样式设置，默认为 .postip
-	content:{string} 相对弹出层内容设置，如未填或为空时，内容为触发层rel值，可以是innerHTML
-	otip:{object} 默认js会构建一个tip，指定otip对象后，tip为otip对象


		
Y.Postip实例对象的方法

-	init:初始化，参数为options
-	buildParam:构造配置项，在init的时候调用
-	render:渲染，init在new的时候调用，render可以在运行时任意时刻调用，参数为options，其成员可覆盖原参数
-	parseParam:重置配置项，在render的时候调用
-	bindEvent:注册事件
-	posTip:重新定位相对弹出层，参数为触发对象
-	show:显示相对提示层
-	hide:隐藏相对提示层
-	getLeft:获得相对提示层相对于触发层的左边距，参数为(pos.h,触发层,相对提示层)
-	getTop:获得相对提示层相对于触发层的顶边距，参数为(pos.v,触发层,相对提示层)
