<template>
    <div class="container mt-5">

        <div class="card">
            <div class="card-header">
                Tasks
            </div>
            <table class="table">
                <thead>
                    <tr>
                        <th scope="col">Items</th>
                        <th scope="col">Status</th>
                        <th scope="col">Action</th>

                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, key) in list" :key="key">
                        <td>{{item.item}}</td>
                        <td>{{format_date(item.date)}}</td>
                        <td> 
                            <button type="submit" class="btn btn-danger" @click="deleteItem(item)">Delete</button> 
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
<script>
import moment from 'moment'

export default {
    name: 'ItemDelete',
    props: {
        list:Array,
        delete:Function,
    },
    methods :{
            format_date(value){
                if (value) {
                    return moment(String(value)).format('D MMMM YYYY HH:mm')
                }
            },

            deleteItem(item){
		  this.delete(item)
	  }
           
    }
    }

</script>
