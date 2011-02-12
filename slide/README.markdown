# Slide

- [Tab Demo](http://taobao-wd.github.com/slide/demo/tab.html)
- [Slide Demo](http://taobao-wd.github.com/slide/demo/slide.html)
- [none-effect DEMO](http://taobao-wd.github.com/slide/demo/tb-slide-none.html)
- [fade-effect DEMO](http://taobao-wd.github.com/slide/demo/tb-slide-fade.html)
- [v-slide DEMO](http://taobao-wd.github.com/slide/demo/tb-slide-v-scroll.html)
- [h-slide DEMO](http://taobao-wd.github.com/slide/demo/tb-slide-scroll.html)
- [carsousel DEMO](http://taobao-wd.github.com/slide/demo/tb-carousel.html)
- [le.taobao.com DEMO](http://taobao-wd.github.com/slide/demo/le.taobao.com.html)
- [mojo DEMO](http://taobao-wd.github.com/slide/demo/mojo-slide.html)
- [lazyload Demo](http://taobao-wd.github.com/lazy-mojo/demo.html)

# Doc

-	tab,slide,carousel本质上是一个东西，都是tab标签+内容切换,不同的仅是切换方式、自动播放、标签个数等
-	Y.Slide伴随典型的tab结构，可通过css配置样式，但基本结构应当固定
-	Y.Slide的适用范围：幻灯、静态页签的切换、自动轮播等，适用范围仍有限制
-	开发者需要根据实际情况做适当扩展，扩展程度自由掌握
-	在ie6，ie7，firefox2,firefox3,opera9,safari4,chrome中测试通过

典型的html结构

	<div id="J_tab_3" class="t-slide-2 mt20">
	  <ul class="tab-nav clearfix">
		<li class="selected"><a href="#">1</a></li>
		<li><a href="">2</a></li>
		<li><a href="">3</a></li>
		<li><a href="">4</a></li>
	  </ul>
	  <div class="tab-content">
		<div class="tab-pannel"><p><img src="img/s1.jpg" /></p></div>
		<div class="tab-pannel hidden"><p><img src="img/s2.jpg" /></p></div>
		<div class="tab-pannel hidden"><p><img src="img/s3.jpg" /></p></div>
		<div class="tab-pannel hidden"><p><img src="img/s4.jpg" /></p></div>
	  </div>
	</div>

须知

-	J_tab_3，必须指定
-	ul.tab-nav,控制导航,必须指定,容器内容可以为空，默认指定自然数为下标
-	ul.tab-nav li.selected,控制tab页签,若有li，则必须指定
-	div.tab-content，内容容器，必须指定
-	div.tab-content div.tab-pannel，内容面板，必须指定

基本原型结构如下：标注部分为必要部分

![结构图](http://cubee.github.com/doc/assets/images/tab_html_code.gif)

-	样式的定制
-	如果是图片轮播，div.tab-content需要指定宽高，超出部分隐藏掉，div.tab-pannel的宽高都为100%即可，这里需要指定div.tab-content的position:relative。
-	普通tab点击切换（无特效），内容部分高度不定，若带滚动切换效果，则需要制定div.tab-content尺寸
-	基本结构包含导航和内容两部分，“向前”、“向后”的按钮切换由开发者添加,只需保证基本原型html的完整即可
-	控制样式的class name可以配置，需要在js中启动的时候做相应配置，在不配置的情况下，Y.Slide以典型html结构做为默认配置进行渲染

种子的引入,	需要slide.js，引用方法如下

	modules:{
		'slide-skin':{//不提供默认皮肤，开发者自行绑定
			fullpath:'../skin.css',
			type:'css'
		},
		'slide':{
			fullpath:'../slide.js',
			requires:['slide-skin','node','anim']
		}
	}

新建一个Y.Slide对象

	new Y.Slide('J_tab_1',{
		autoSlide:false,
		eventype:'click'
	});

另外一个例子

	new Y.Slide('J_tab_1',{
		eventype:'click',//tab上的触发事件
		effect:'v-slide',//切换效果
		autoSlide:true,//自动播放
		timeout:2000,//切换时间间隔
		speed:0.5,//切换速度，越小越快
		hoverStop:true//鼠标经过内容是否停止播放
	});

使用：`new Y.Slide(id,options)`

配置：		

-	autoSlide:{boolean} 是否自动播放，默认为false
-	speed:{float} 切换特效的速度，默认为0.5
-	timeout:{Number} 切换时间间隔,默认为1000毫秒
-	effect:{string} 特效类型，默认为'none'，取值：'none',无特效,'fade',渐隐,'h-slide',水平切换,'v-slide',垂直切换
-	eventype:{string} 触发tab切换的事件类型，默认为'click',取值：'click',点击，'mouseover',鼠标滑过
-	easing:{string} 切换面板的特效风格，默认为'easeBoth',参考<a href="http://developer.yahoo.com/yui/3/api/Easing.html" target=_blank>YUI doc
-	hoverStop:{boolean} 鼠标悬停面板上是否停止播放，默认为true
-	selectedClass:{string} tab选中时的class name，默认为'selected'
-	conClass:{string} 容器的class name，默认为't-slide'，目前没有用
-	navClass:{string} tab容器的class name，默认为'tab-nav'
-	contentClass:{string} tab内容容器的class name,默认为tab-content
-	pannelClass:{string} tab面板的class name，默认为tab-pannel
-	id:{string} hook
-	before_switch:{function} 切换之前执行的动作，参数同switch事件的参数，返回true，继续执行，返回false，停止执行
-	ready:{function} 初始化完成后的回调，参数同switch事件的参数，当前index为0
-	carousel:{boolean} 是否以旋转木马形式播放，默认为false
-	reverse:{boolean} "播放下一个"和"播放上一个"对调，默认为false
				
Y.Slide实例对象的方法

-	init:初始化，参数为options
-	previous:滚动到上一个
-	next:滚动到下一个
-	goto:跳转到指定的tab，参数为index:0,1,2,3..，执行before_switch
-	switch_to:跳转到指定的tab，参数为index:0,1,2,3...，和goto的不同是，不执行执行before_switch
-	play:开始播放
-	stop:停止播放

Y.Slide的事件

- switch:切换时发生，不执行before_switch 回调参数为{index:index,navnode:navnode,pannelnode:pannelnode}
