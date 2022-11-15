<template>
    <div class="main-window"> 
        <div class="new-order-button__wrapper">
            <button class="new-order-button"><span>НОВЫЙ ЗАКАЗ</span></button>
            <div class="decoration"></div>
        </div>
        <FilterForm />
        <Table />
    </div>
</template>

<script>
  import FilterForm from '@/components/FilterForm.vue'
  import Table from '@/components/Table.vue'

  export default {
    components: {
        FilterForm, Table
    }
  }
</script>

<style>
    @import url('../styles/MainWindow.css');
</style>