# Checkall

- [Demo](http://taobao-wd.github.com/checkall/demo/demo.html)

# Info

种子的引入

	YUI({charset:'utf-8', modules:{
			'checkall': {
				fullpath: '../checkall.js',
				type: 'js',
				requires: ['node']
			}
	}}).use('checkall', function(Y){
		//your code
	});

生成实例


	//生成实例
	var c = new Y.Checkall({
		node:[Y.one('#J_checkall_1'),Y.one('#J_checkall_2')],
		/*node:Y.one('#J_check_all_1')*/
		nodelist:Y.all('.checklist'),
		inverse:[Y.one('#J_inverse_1'),Y.one('#J_inverse_2')]
		/*inverse:Y.one('#J_check_all_1')*/
	}).on('check',function(o){
		Y.log(Y.dump(o));
	});

调用

	c.invert();//反选

API

配置	

- node:{string|array} 必填，全选checkbox的YUI node，类型可以为数组，也可以为一个YUI node
- nodelist:{YUI nodelist} 必填  checkbox items
- inverse:{string|array} 选填 反选按钮，参数可以为数组，也可以为一个YUI node

实例方法

- invert:反选			

事件类型：

- check:每次点击触发的切换事件，带回

	{
	checked:{array}(当前checked的节点数组，数组成员为YUI node)
	unchecked:{array}(当前unchecked的节点数组，数组成员为YUI node)
	}
		
