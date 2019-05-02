<template>
	<ul class="list-reset inline flex justify-center border-b-4 mb-0">
		<li
			class="top-menu-item hover:bg-grey-light cursor-pointer"
			v-for="category in categories"
			:key="category" >
			{{category}}
		</li>
		<li class="top-menu-item hover:bg-grey-light cursor-pointer" @click="triggerShowAddCategory">➕</li>
	</ul>
</template>

<script>
    export default {
        name: "NavBar",
		props: ['categories'],
		methods: {
            triggerShowAddCategory() {
                this.$emit('triggerShowAddCategory')
			}
		}
    }
</script>

<style scoped>
	.top-menu-item {
		@apply .p-4 .inline .bg-grey-lighter  .uppercase .font-black;
	}
</style>
