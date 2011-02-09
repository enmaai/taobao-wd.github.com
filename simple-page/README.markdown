# Spage

- [Demo1](http://taobao-wd.github.com/simple-page/demo/demo.html)
- [Demo2](http://taobao-wd.github.com/simple-page/demo/demo2.html)

# Doc

-	基于YUI3
-	js实现列表项的分页逻辑
-	提供简单的分页的页签，页码为自动生成
-	适用与小容器中数据量不大的datalist分页，对于庞大数据量的情况请配合Y.pagination使用
-	在ie6,ie7,firefox2,firefox3.0/3.5/3.6,safari4.0,opera9.62,chrome3.0下测试通过

种子的引入

	YUI({charset:'utf-8', modules:{
			'spage': {
				fullpath: '../simplepage.js',
				type: 'js',
				requires: ['node']
			}
	}}).use('spage', function(Y){
		//your code
	});

新建一个Y.Spage对象

	//生成实例
	var p = new Y.Spage(Y.all('#Hook .item'),'Page',{
		step:4,
		index:2,
		selected_class:'on'
	}).on('pagechange',function(o){
		Y.log(Y.dump(o));
	});	
	//参数说明：
	//setp默认为10
调用

	p.render({index:5});//显示第五页

Y.Spage构造器

使用：	

	new Y.Spage(nodelist,id,config);

参数：	

-	nodelist:{yui3-nodelist}yui3 nodelist对象
-	id:{string}显示页签的容器id
-	config:{object}配置项
			
配置：	

-	selected_class:{string} 可选，选中的a的className，默认为'selected'
-	step:{number} 每页item个数
-	index:{number} 当前页
	
Y.Spage实例对象的方法和事件
	
-	实例方法：render,重新设置分页
-	事件类型:pagechange:切换页码事件，带回

	{
	rear:rear,
	top:top,
	index:index,
	step:that.step
	}
