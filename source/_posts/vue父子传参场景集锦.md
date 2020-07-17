---
date: 2017-12-14
categories: 
- 前端
- Vue
tags:
- Vue
---
# vue父子传参场景集锦(一)

>### 父传子数据,子修改数据,父不改

场景: 列表(父组件)点击,弹出表单并传递当前行数据到表单(子组件),表单使用双向绑定(elementUI el-form),需求是实现表单可编辑(v-model),且不修改列表数据(取消时列表数据未变).

1. 直接使用props属性内数据,可以实现表单和列表数据修改同步(不符子不改父的原则),切换点击行时可以同步当前行数据

   ```js
   <Edit :articleForm='rowData' />//父调用子组件 rowData:{title:"xx",content:"xx"}
	export default {
   		data() {
			return {
				rowData:{},
			}
		},
		methods(){
		   	edit(row) {//行点击事件
                this.rowData = row;
            },
		}
	}
   ```

   ```js
   <el-form :model="articleForm" ref='articleForm'>//子组件
   	<el-form-item label="标题">
   		<el-input v-model="articleForm.title" placeholder="请输入标题"></el-input>
   	</el-form-item>
   </el-form>
   export default {
   	data() {
   		return {
   		};
   	},
   	props: [
   		'articleForm',
   		'type',
   		'reload'
   	],
   }
   ```


2. 在data里将父组件传递的数据进行一次赋值(别名),实现父子组件取消双向绑定(Object.assign).(无法在切换行时将父组件传递的props同步到articleForm数据)

   ```js
   <Edit :rowData='rowData' />//父调用子组件 rowData:{title:"xx",content:"xx"}
   export default {
   		data() {
			return {
				rowData:{},
			}
		},
		methods(){
		   	edit(row) {//行点击事件,copy行数据
                this.rowData = row;
            },
		}
	}
   ```

   ```js
   <el-form :model="articleForm" ref='articleForm'>//子组件
   	<el-form-item label="标题">
   		<el-input v-model="articleForm.title" placeholder="请输入标题"></el-input>
   	</el-form-item>
   </el-form>
   export default {
   	data() {
   		return {
   			//articleForm:this.rowData,//别名
   			articleForm:Object.assign({},this.rowData)//别名,并避免绑定
   		};
   	},
   	props: [
   		'rowData',
   		'type',
   		'reload'
   	],
   }
   ```
3. props接受数据,使用computed赋值,实现切换行更改articleForm.

   ```js
   <Edit :rowData='rowData' />//父调用子组件 rowData:{title:"xx",content:"xx"}
    export default {
   		data() {
			return {
				rowData:{},
			}
		},
		methods(){
		   	edit(row) {//行点击事件
                this.rowData = row;
            },
		}
	}
   ```

   ```js
   <el-form :model="articleForm" ref='articleForm'>//子组件
   	<el-form-item label="标题">
   		<el-input v-model="articleForm.title" placeholder="请输入标题"></el-input>
   	</el-form-item>
   </el-form>
   export default {
        data() {
            return {
            };
        },
        props: [
            'rowData',
            'type',
            'reload'
        ],
        computed: {
            articleForm: function() {
             	//return this.rowData//切换行可以同步父组件传递的新数据,且子组件会更改父组件数据,等同于方案1
                return Object.assign({},this.rowData)//切换行可以同步父组件传递的新数据,但子组件无法编辑数据
            }
        },
	}
   ```
4. 在data里将父组件传递的数据进行copy,实现父子组件取消双向绑定.使用watch监听实现切换行时将父组件数据同步到articleForm数据,符合需求

   ```js
   <Edit :rowData='rowData' />//父调用子组件 rowData:{title:"xx",content:"xx"}
    export default {
   		data() {
			return {
				rowData:{},
			}
		},
		methods(){
		   	edit(row) {//行点击事件
                this.rowData = row;
            },
		}
	}
   ```

   ```js
   <el-form :model="articleForm" ref='articleForm'>//子组件
   	<el-form-item label="标题">
   		<el-input v-model="articleForm.title" placeholder="请输入标题"></el-input>
   	</el-form-item>
   </el-form>
   export default {
   	data() {
   		return {
   			img_file: [],
   			articleForm:{}
   			//articleForm:Object.assign({},this.rowData)//别名,并copy
   		};
   	},
   	props: [
   		'rowData',
   		'type',
   		'reload'
   	],
   	watch:{
	        rowData: {
	            deep: true,
	            immediate: true,//立刻监听,不用在data里进行第一次赋值
	            handler: function (val, oldVal) { 
	                this.articleForm = Object.assign({},val);
	            },
	        }
		},
    }
   ```
5. 在父组件进行数据源深copy,子组件就可以随意了,符合需求(最佳)

   ```js
   <Edit :articleForm='rowData' />//父调用子组件 rowData:{title:"xx",content:"xx"}
   	export default {
   		data() {
			return {
				rowData:{},
			}
		},
		methods(){
		   	edit(row) {//行点击事件,copy行数据
                this.rowData = Object.assign({},row);
            },
		}
	}
   ```

   ```js
   <el-form :model="articleForm" ref='articleForm'>//子组件
   	<el-form-item label="标题">
   		<el-input v-model="articleForm.title" placeholder="请输入标题"></el-input>
   	</el-form-item>
   </el-form>
   export default {
   	data() {
   		return {
   			img_file: [],
   		};
   	},
   	props: [
   		'articleForm',//或者使用computed赋值(改名)
   		'type',
   		'reload'
   	],
	}
   ```