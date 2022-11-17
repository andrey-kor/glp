<template>
    <div class="main-window"> 
        <div class="new-order-button__wrapper">
            <button class="new-order-button"><span>НОВЫЙ ЗАКАЗ</span></button>
            <div class="decoration"></div>
        </div>
        <FilterForm 
            @sortOrders="sortOrders"
        />
        <Table v-bind:orders="filteredOrders" />
    </div>
</template>

<script>
  import FilterForm from '@/components/FilterForm.vue'
  import Table from '@/components/Table.vue'

  export default {
    props: ['orders'],
    data() {
        return {
            sortedOrders: this.orders
        }
    },  
    components: {
        FilterForm, Table
    },
    methods: {
        sortOrders({filterType, value = ''}) {
            const context = this
            
            if (filterType === 'textArea') {
                
                const searchedProps = [
                    'state', 'date', 'weight', 'type', 'orderNum', 
                    'pointA', 'pointB', 'executor', 'cost', 'payment'
                ]

                
                this.sortedOrders = this.orders.filter((order) => {
                    for (let i=0; i< searchedProps.length; i++) {
                        console.log(order[searchedProps[i]])
                        if (String(order[searchedProps[i]]).toUpperCase().indexOf(value.toUpperCase()) !== -1) {
                            return true
                        }
                    }
                })
                
            }

            if (filterType === 'dataArea') {
                console.log(value)
            }

            if (filterType === 'today') {
                this.sortedOrders = this.orders.filter((order) => {
                    return order.date === '20.07.2021'
                })
            }

            if (filterType === 'tomorrow') {
                this.sortedOrders = this.orders.filter((order) => {
                    return order.date === '21.07.2021'
                })
            }

            if (!this.sortedOrders) {
                this.sortedOrders = this.orders
            }
        },
    },
    computed: {
        filteredOrders() {
            if (this.sortedOrders) {
                return this.sortedOrders
            }
            return this.orders
        },
    }
  }
</script>

<style>
    @import url('../styles/MainWindow.css');
</style>