<template>
	<AddItem :list="todo" />
	<List :list="todo" :delete="deleteItem" />
</template>

<script>
import AddItem from './components/AddItem.vue'
import List from './components/List.vue'

export default {
	name: 'App',
	components: {
		AddItem,
		List
	},
	data () {
		return {
			todo: []
		}
	},
	methods: {
		deleteItem(item){
			this.$data.todo = this.$data.todo.filter(function(value, index, arr){ 
				if(value == item){ return false; }
				else{ return true; }
			});
		}
	}
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
