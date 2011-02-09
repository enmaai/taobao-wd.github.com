# 日期级联

- [Demo](http://taobao-wd.github.com/datecascade/demo/index.html)

# Doc

-	可以通过扩展Y.DateCascade来实现时间级联选择
-	初始化文本输入框后，级联日期菜单将改变获取的日期回填至初始化文本输入框
-	获取初始日期优先级：1.文本输入框value 2.参数配置中 defaultDate 值设定 3.中途修改时间 render
-	可设置日期范围，形如 2010/5/21 or 2010-5-21格式

种子的引入,	需要引入datecascade.js

	modules:{
		'datecascade':{
			fullpath:'../datecascade.js?',
			type:'js',
			requires:['node']
		}
	}
	
新建一个Y.DateCascade对象

	var Demo1 = new Y.DateCascade(id,config);
	//id 为初始化输入框时的id或dom Object
	//id 可以是Object：Y.one('.J_demo1') 或 idname：'id'
	
构造说明
		
说明：日期级联选择构造器，通过new Y.DateCascade来render一个包含年月日期的三组下拉菜单

使用:`new Y.DateCascade(options)`

配置：		

-	defalutDate:{string} 初始日期，如为空时下拉菜单不会有选中
-	dateStart:{string} 可选择开始日期，默认为 1930/1/1
-	dateEnd:{string}可设置结束日期，默认为客户端获取的今日
	
Y.DateCascade 实例对象的方法
	
		
方法：
			
-	init:初始化，参数为options
-	buildParam:构造配置项，在init的时候调用
-	render:渲染，init在new的时候调用，render可以在运行时任意时刻调用，参数为options，其成员可覆盖原参数
-	buildSelector:初始化时渲染组件HTML
-	parseParam:重置配置项，在render的时候调用
-	bindEvent:注册事件
-	_selectedDate:返回选择日期，年月日任意一项不能为空
-	makeYear:创建年下拉菜单项
-	makeMonth:创建月下拉菜单项
-	makeDate:创建日下拉菜单项
-	createMonth:获得月份上下限
-	createDate:获得日期上下天数
-	updateDate:给文本框写入已选择日期
-	_Fn:内部依赖常用方法：如：isLeapYear(是否闰年)  insertAfter(节点后插入)
			
		
	

