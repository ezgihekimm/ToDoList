<template>

 <HelloWorld msg="Welcome to Your Vue.js App"/>
 <AddItem :list="todo" />
 <ItemDelete :list="todo" :delete="deleteItem"/>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import AddItem from './components/AddItem.vue'
import ItemDelete from './components/ItemDelete.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    ItemDelete,
    AddItem
  },
  data(){
    return {todo:[]
    }
  },
  methods: {
		deleteItem(item){
			this.$data.todo = this.$data.todo.filter(function(value, index, arr){ 
				if(value == item){ return false; }
				else{ return true; }
			});
		}
}}
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
