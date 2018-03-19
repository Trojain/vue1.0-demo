vue1.0+webpack+es6(非vue-cli)
	运行方式：npm run dev

	1.vue-loader(基于webpack，通过webpack编译 .vue文件)
	
		.vue文件中放置的是vue组建代码：
		
			<template>
				html
			</template>
			
			<script>
				js
			</script>
			
			<style>
				css
			</style>
	
	
	
	2.简单的目录结构：
	
		|- index.html
		|- main.js           入口文件
		|- App.vue           vue文件
		|- package.json      工程文件(项目依赖、名称、配置)   npm init --yes 生成
		|- webpack.config.js webpack配置文件    
		|- components        放置组件的文件夹
		|--- Other.vue        其他组件
	
	
	
	
	3.配置webpack.config.js
	
		module.exports={
			entry:'./main.js',	//入口
			output:{	//出口
				path:__dirname,	//当前路径
				filename:'build.js'	//打包成build.js
			},
			module:{
				loaders:[
					{test:/\.vue$/,loader:'vue'}    //将.vue结尾的文件用vue-loader来编译
					{test:/\.js$/,loader:'babel',exclude:/node_modules/},	//将.js结尾的文件用babel来编译，除了node_modules下的文件
				]
			}
		}

		
		
	4.修改package.json中scripts (自动刷新热加载)
		  "scripts": {
			"dev": "webpack-dev-server --inline --hot"
		  }
	
	
	
	5.安装模块依赖：(package.json中可查看已看装的模块)
		(开发依赖的模块用 --save-dev  会在package.json的devDependencies中)
		(必须依赖的模块用 --save   会在package.json的dependencies中)
		(以下安装的依赖都是基于vue1.0，并非2.0)
	
		5.1 安装1.0.28版本的vue依赖：	
			cnpm install vue@1.0.28 --save
		
		5.2	安装webpack依赖：
			cnpm install webpack webpack-dev-server --save-dev
						
		5.3 安装vue-loader@8.5.4依赖：(用来编译.vue文件)
			cnpm install vue-loader@8.5.4 --save-dev
			
		5.4	安装vue-html-loader、css-loader、vue-style-loader、vue-hot-reload-api@1.3.2依赖：(分别是用来编译.vue中的template、style、script)
			cnpm install vue-html-loader css-loader vue-style-loader vue-hot-reload-api@1.3.2 --save-dev
		
		5.5	安装babel依赖：(用来编译ES6)
			cnpm install babel-loader babel-core babel-plugin-transform-runtime babel-preset-es2015 babel-runtime --save-dev
			
			
			

	6.关于ES6的模块化：
		导出模块：export default{}
		导入模块：import 模块名 from 地址