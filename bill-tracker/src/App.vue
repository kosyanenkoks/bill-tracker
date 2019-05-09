<template>
    <main>
        <AddCategory v-if="shouldShowAddCategory" v-on:addCategory="addCategory"/>
        <div v-else>
            <AddBill v-if="shouldShowAddBill" :categories=categories v-on:addBill="addBill"/>
            <div v-else>
                <NavBar :categories=categories v-on:triggerShowAddCategory=triggerShowAddCategory />
                <div class="container flex">
                    <div class="w-1/2">
                        <BillsTable />
                    </div>
                    <div class="w-1/2">
                        <Chart />
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
    import AddCategory from './components/AddCategory.vue'
    import AddBill from './components/AddBill.vue'
    import NavBar from './components/NavBar.vue'
    import Chart from './components/Chart.vue'
    import BillsTable from './components/BillsTable.vue'

    export default {
        name: 'App',
        components: {
            AddCategory,
            AddBill,
            Chart,
            BillsTable,
            NavBar
        },
		data() {
            return {
                bills: [],
				categories: [],
                shouldShowAddCategory: true,
                shouldShowAddBill: true
			}
		},
		methods: {
            addCategory(category) {
                this.categories.push(category);
                this.shouldShowAddCategory = false;
			},
            triggerShowAddCategory() {
                this.shouldShowAddCategory = true
			},
            addBill(bill) {
                this.bills.push(bill);
                this.shouldShowAddBill = false;
            }
		},
		watch: {
            bills() {
              localStorage.setItem('bills', JSON.stringify(this.bills))
            },
            categories() {
                localStorage.setItem('categories', JSON.stringify(this.categories))
            }
        },
		mounted() {
            if (localStorage.getItem('bills')) {
                this.bills = JSON.parse(localStorage.getItem('bills'))
            }
            if (localStorage.getItem('categories')) {
                this.categories = JSON.parse(localStorage.getItem('categories'))
			}

			if (!this.bills.length && !this.categories.length) {
			    this.shouldShowAddCategory = true
			}
		}
    }
</script>


<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
