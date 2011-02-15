# 基于yui3.3.0 的所有自定义模块的combine

- [Demo](http://taobao-wd.github.com/full-combine/demo.html)

定义模块的时候，指定每个模块的path和root，并指定combine参数为true,例如

	var mods = {
		calendar:{
			path:'index-v2/js/calendar.js',
			root:'apps/lottery/00012/',
			combine:true,
			requires:['node','calendar-skin']
		},
		'calendar-skin':{
			path:'index-v2/css/calendar.css',
			root:'apps/lottery/00012/',
			combine:true,
			type:'css'
		}
	};
