<template>
	<h1 @click="change">{{msg}}</h1>
	<my-other></my-other>
</template>

<script>
	import Other from './components/Other.vue'  //引用Other.vue组件
	export default{
		data(){
			return {
				msg:'vue1.0  ^_^'
			}
		},
		methods:{
			change(){
				this.msg == '666' ? this.msg='vue1.0 demo' : this.msg='666';
			}
		},
		components:{
			'my-other':Other
		}
	}
</script>

<style>
	body{
		color: #666;
	}
</style>