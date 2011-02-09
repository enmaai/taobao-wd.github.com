# Box

- [Demo](http://taobao-wd.github.com/box/demo/demo-box.html)

# Info


-	基于YUI3-overlay
-	可以通过扩展Y.Box来实现自定义弹框
-	弹框默认宽度是300px，默认高度是auto，高度可以随着内容增多而变化，宽度不会变化
-	弹框宽度设为auto的时候，在ie6下表现和其他A级浏览器不尽一致，因此不建议使用宽度auto配置
-	皮肤需要在加载的时候作为box的子模块引入进来
-	可以层叠多个弹框
-	safari,opera下弹层默认无法遮盖media控件，chrome下弹层默认不完全遮盖media控件,可以通过配置antijam为 true来隐藏media控件
-	在ie6，ie7，firefox2,firefox3,opera9,safari4,chrome中测试通过


需要两个文件，皮肤skin.css和box.js，引用方法如下

	modules:{
		'box-skin-default':{//默认皮肤
			fullpath:'../skin/default.css',
			type:'css'
		},
		'box-skin-sea':{//另外一套皮肤
			fullpath:'../skin/sea.css',
			type:'css'
		},
		'box':{
			fullpath:'../box.js',
			requires:['box-skin-sea','node','overlay','dd-plugin']
		}
	}


新建一个Y.Box对象

	var box = new Y.Box({
		head:'<span class="title">the title</span><a class="close">[x]',
		body:'body',
		foot:'foot'
	}).render();
	
创建一个Y.Box.alert,带入回调并进行配置：标题、可拖拽、显示回调、加载的回调等等

	var box = Y.Box.alert('哈哈哈',function(box){
		alert('点击ok');
		Y.log('点击ok');
	},{
		title:'title',
		draggable:true,
		afterDrag:function(box){
			Y.log('拖拽over');
		},
		afterShow:function(box){
			Y.log('显示over');
		},
		afterHide:function(box){
			Y.log('隐藏over');
		},
		onload:function(box){
			Y.log('初始化over');
		}
		
	});
	
创建一个Y.Box.confirm，带入回调函数并进行配置：标题，“否”的回调，拖拽的回调，显示和隐藏的回调等等

	var box = Y.Box.confirm('confirm',function(box){
		alert('点击yes');
		Y.log('点击yes');
	},{
		anim:false,
		title:'confirm title',
		no:function(box){
			alert('点击no');
			Y.log('点击no');	
		},
		cancleBtn:true,
		cancleTxt:'cancle',
		draggable:true,
		afterDrag:function(box){
			Y.log('拖拽confirm over');
		},
		afterShow:function(box){
			Y.log('显示comfirm over');
		},
		afterHide:function(box){
			Y.log('隐藏comfirm over');
		},
		onload:function(box){
			Y.log('初始化comfirm over');
		}
	});
	

Y.Box实例对象的方法
	
方法：
			
-	init:初始化，参数为options
-	bringToTop:将box的z-index调到所有box之上
-	render:渲染，init在new的时候调用，render可以在运行时任意时刻调用，参数为options，其成员可覆盖原参数
-	close:关闭，并将窗口删除
-	hide:隐藏，不会删除窗口
-	show:显示窗口
-	buildParam:构造配置项，在init的时候调用
-	parseParam:重置配置项，在render的时候调用
-	addMask:添加遮罩
-	removeMask:删除遮罩
-	hideMedias:隐藏media干扰物
-	showMedias:解除media干扰物隐藏

**Y.Box.alert**
		
说明:alert弹出框，基于Y.Box的一种定制

使用：	

	Y.Box.alert(msg,callback,options)

参数：		
			
- msg:{string} 消息体
- callback:{function} 点击确定的回调，参数为box，默认点击确定会关闭窗口
- options:{object} 配置项
			
配置：		

-	title:{string} 标题
-	closeable:{boolean} 是否有关闭按钮，默认为true
-	closeText:{string} 可以自定义按钮
-	btnText:{string} 确定按钮的文案
-	（其他字段同Y.Box的 options）
		
**Y.Box.confirm**
	
说明:comfirm弹出框，基于Y.Box的一种定制
使用：	

	Y.Box.confirm(msg,callback,options)

参数：		

- msg:{string} 消息体
- callback:{function} 点击确定的回调，参数为box，默认点击确定会关闭窗口
- options:{object} 配置项
			
配置：		
			
-	title:{string} 标题
-	yes:{function} 点击是的回调，参数为box，默认点击会关闭，此项会覆盖callback
-	no:{function} 点击否的回调，参数为box
-	yesText:{string} 按钮“是”的文案
-	noText:{string} 按钮"否"的文案
-	cancleBtn:{boolean} 是否显示"关闭"按钮，默认为true
-	cancleText:{string} 按钮“取消”的文案
-	（其他字段同Y.Box的 options）

**Y.Box**
	
说明：窗口构造器，通过new Y.Box来render一个box，可以使用Y.Box定制自己的alert、comfirm、prompt等等

使用：	

	new Y.Box(options);

配置：		

-	head:{string} box头部
-	body:{string} box主题部分
-	foot:{string} box尾部
-	fixed:{boolean} true,box不会随着窗口滚动而滚动，false，box会随着窗口滚动而滚动，默认为true（ie6下始终会跟随页面滚动而滚动）
-	afterDrag:{function} 拖拽结束的回调，参数为box本身
-	draggable:{boolean} 是否可拖拽,默认为true
-	resizeable:{boolean} 是否可resize，默认为false（未实现）
-	afterResize:{function} resize结束的回调，参数为box，（未实现）
-	shownImmediately:{boolean} 是否初始化完成立即显示，默认为true	  
-	afterHide:{function} 隐藏完毕后的回调，参数为box
-	afterShow:{function} 显示完成后的回调，参数为box
-	onload:{function} 初始化完成后的回调，在render后立即执行，参数为box
-	modal:{boolean} 是否带阴影，默认为false，阴影的动画效果未实现
-	beforeUnload:{function} 窗口关闭之前的回调,参数为box
-	afterUnload:{function} 窗口关闭之后的回调,参数为box		
-	antijam:{boolean} 是否隐藏media干扰物，默认为false
-	maskOpacity:{float} 设定遮盖层的透明度，范围是[0,1]，默认为0.6，当modal为true时才起作用

