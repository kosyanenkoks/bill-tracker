<template>
	<div>
		<h1>Enter a new bill</h1>
		<p></p>
		<div>
			<input type="text" placeholder="Set amount" v-model="amount">
			<button @click="handleClick">Add</button>

			<select v-model="category">
				<option
					v-for="category in categories"
					:value="category"
					:key="category">
					{{ category }}
				</option>
			</select>
		</div>
	</div>
</template>

<script>
    export default {
        name: "AddBill",
		props: ['categories'],
		data: function () {
			return {
			    category: this.categories[0],
			    amount: 0
			}
        },
		 methods: {
            handlclick: function () {

            }
		 }
    }
</script>

<style scoped>

</style>