<template>
	<div class="container">
		<div class="card">
			<div class="card-header">
				Add a task
			</div>
			<div class="card-body">
				<form @submit.prevent="onSubmit">
					<div class="mb-3">
						<label for="exampleInputEmail1" class="form-label">Item</label>
						<input v-model="input" type="text" class="form-control" id="exampleInputEmail1" placeholder="What do you want to do?" autocomplete="off">
					</div>
					
					<button v-if="!isSubmitting" type="submit" class="btn btn-primary">Submit</button>

					<button v-if="isSubmitting" class="btn btn-primary" type="button" disabled>
						<span class="spinner-border spinner-border-sm" role="status" aria-hidden="true"></span>
						<span class="visually-hidden">Loading...</span>
					</button>

				</form>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'AddItem',
	props: {
		list: Array,
	},
	data () {
	return {
	  	input: "",
	  	isSubmitting: false,
	}
  },
  methods: {
	onSubmit () {
		this.$props.list.push({item: this.$data.input, date: new Date()})
		this.$data.isSubmitting = true;
		setTimeout(() => {
			this.$data.isSubmitting = false;
			this.input = ""
		}, 100)
	}
  }
}
</script>

<style scoped>

</style>
