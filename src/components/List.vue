<template>
	<div class="container mt-4">
		<div class="card">
			<div class="card-header">
				Tasks
			</div>
			<div class="card-body">
				
				<table class="table table-borderless" v-if="isArrayAvailable">
					<thead>
						<tr>
							<th scope="col">Item</th>
							<th scope="col">Status</th>
							<th scope="col">Action</th>
						</tr>
					</thead>
					<tbody>
						<tr v-for="item in list" :key="item.date">
							<td>{{item.item}}</td>
							<td>{{format_date(item.date)}}</td>
							<td>
								<button type="submit" class="btn btn-danger" @click="deleteItem(item)">Delete</button>
							</td>
						</tr>
					</tbody>
				</table>

				<div v-if="!isArrayAvailable">Liste Bos</div>

			</div>
		</div>
	</div>
</template>

<script>
import moment from 'moment'

export default {
	name: 'List',
	props: {
		list: Array,
		delete: Function,
	},
	data () {
		return{
			isArrayAvailable: false,
		}
	},
	watch: {
		list: {
			handler: function () {
				if(this.list.length > 0){ this.isArrayAvailable = true }
				else{ this.isArrayAvailable = false }
				console.log('caught!');
			},
			deep: true
		}
	},
	methods: { 
	  format_date(value){
		 if (value) {
		   return moment(String(value)).format('D MMMM YYYY HH:mm')
		  }
	  },
	  deleteItem(item){
		  this.delete(item)
	  }
   },
}
</script>

<style scoped>

</style>
