<template>
    <div class="main-window"> 
        <div class="new-order-button__wrapper">
            <button 
                class="new-order-button"
                @click.prevent
            ><span>НОВЫЙ ЗАКАЗ</span></button>
            <div class="decoration"></div>
        </div>
        <FilterForm 
            @sortOrders="sortOrders"
            :="{totalCount, todayCount, tomorrowCount}"
        />
        <Table :orders="filteredOrders" />
    </div>
</template>

<script>
  import FilterForm from '@/components/FilterForm.vue'
  import Table from '@/components/Table.vue'

  export default {
    props: {
        orders: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            sortedOrders: this.orders,
        }
    },  
    components: {
        FilterForm, Table
    },
    methods: {
        sortOrders(filters) {
            const context = this
            
            const textFilter = filters[0].value
            const searchedProps = [
                'state', 'date', 'weight', 'type', 'orderNum', 
                'pointA', 'pointB', 'executor', 'cost', 'payment'
            ]
            this.sortedOrders = this.orders.filter((order) => {
                for (let i=0; i< searchedProps.length; i++) {
                    if (String(order[searchedProps[i]]).toUpperCase().indexOf(textFilter.toUpperCase()) !== -1) {
                        return true
                    }
                }
            })
            
            const dateFilter = filters[1].value
            try {
                let [dateFrom, dateTo] = dateFilter.split('').filter((letter) => letter !== ' ').join('').split('-') // dd.mm.yyyy
                dateFrom = new Date(Date.parse(dateFrom.split('.').reverse()))
                dateTo = new Date(Date.parse(dateTo.split('.').reverse())) 
            
                this.sortedOrders = this.sortedOrders.filter((order) => {
                    const orderDate = this.stringToDaye(order.date)
                    return (orderDate >= dateFrom && orderDate <= dateTo)
                })
            }
            catch (e) {}

            const dayFilter = filters[2].value
            if (dayFilter === 'today') {
                this.sortedOrders = this.sortedOrders.filter((order) => {
                    const orderDate = this.stringToDaye(order.date)
                    return +orderDate === +this.TODAY
                })
            }
            if (dayFilter === 'tomorrow') {
                this.sortedOrders = this.sortedOrders.filter((order) => {
                    const orderDate = this.stringToDaye(order.date)
                    return +orderDate === +this.TOMORROW
                })
            }

            if (dayFilter === 'all') {
                this.sortedOrders = this.sortedOrders
            }

            if (!this.sortedOrders) {
                this.sortedOrders = this.sortedOrders
            }
        },
        stringToDaye(string) {
            return new Date(Date.parse(string.split('.').reverse()))
        }
    },
    computed: {
        TODAY() {
            // let date = new Date()         For demo
            let date = new Date(2021, 6, 20) // 20.07.2021
            console.log('today: ', date)
            return date
        },
        TOMORROW() {
            // let date = new Date()         For demo
            let date = new Date(2021, 6, 20) // 21.07.2021
            date.setDate(date.getDate() + 1);
            console.log('tomorrow: ', date)
            return date
        },
        filteredOrders() {
            if (this.sortedOrders) {
                return this.sortedOrders
            }
            return this.orders
        },
        totalCount() {
            return this.orders.length
        },
        todayCount() {
            return this.orders.filter((order) => {
                    const orderDate = this.stringToDaye(order.date)
                    return +orderDate === +this.TODAY
                }).length
        },
        tomorrowCount() {
            return this.orders.filter((order) => {
                    const orderDate = this.stringToDaye(order.date)
                    return +orderDate === +this.TOMORROW
                }).length
        }
    }
  }
</script>

<style>
    @import url('../styles/MainWindow.css');
</style>