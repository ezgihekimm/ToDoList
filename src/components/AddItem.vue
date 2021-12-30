<template>
  <div class="container">
  <h1 class="h text-center">Todos</h1>
  <div class="card">
  <div class="card-header">
    Add a task
  </div>
  <div class="card-body">
  <label for="basic-url" class="form-label">Item</label>
   <div class="input-group mb-3">
  <input v-model="message" type="text" class="form-control " placeholder="What do you want to do?" aria-label="Username">

  
</div>

<p>input:{{message}} </p>

   <a href="#" @click="onbutton" class="btn btn-primary mt-2 " v-if="!available" >Submit</a>
   <button  class="btn btn-primary "  v-if="available" type="button" disabled>
   <span class="spinner-border spinner-border-sm"  role="status" aria-hidden="true"></span>
  
 
</button>
  </div>
</div>
   
  </div>
</template>

<script>
export default {
  name: 'AddItem',
  props: {
    list:Array,
   
  },
  data(){
    return{
      message:'',
      available:false,
    }
  },
  methods:{ onbutton(){
    this.available=true;
    this.$props.list.push({item: this.message,  date: new Date() })
    this.message='',
    
    console.log("eklendi")
    console.log(this.list)
    setTimeout(()=>{
      this.available=false
    }, 500)

  }
   
   
   
 
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
