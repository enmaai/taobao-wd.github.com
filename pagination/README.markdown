# pagination

两个实例代码，实现不一样

- [Demo1](http://taobao-wd.github.com/pagination/demo/pagination.html)
- [Demo2](http://taobao-wd.github.com/pagination2/demo/pagination.html)

# 第2个Demo的Doc,第一个控件的api和它基本上一致

新建一个Y.Pagination对象

	//生成分页控件实例
	var p = new Y.Pagination({
		contentBox: '#page1',
		max: 22,
		index: 10
	});	
	//参数说明：
	//setp默认为7

调用

	p.setMax(50);//设置分页总数为50
	p.setStep(5);//设置分页步长为5
	p.setIndex(13);//设置当前页为13

	
Y.Pagination构造器
		
	new Y.Pagination(config);

配置：	

-	contentBox:{#id} 必选，分页容器id
-	max:{number} 必选，最大页数
-	step:{number} 分页步长
-	index:{number} 当前页
-	jump:{boolean} 是否有跳转，默认为false
			
		
Y.Pagination实例对象的方法和事件:继承自Y.Widget，扩展方法：

-	setMax:设置分页总数
-	setStep:设置分页步长
-	setIndex:设置当前页
			
事件类型：
			
- trigger:点击事件，回调为e对象，包含page(点击的页数)和max(最大页数)属性

