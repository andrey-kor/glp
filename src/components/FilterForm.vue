<template>
    <div class="filter-form">
        <div class="form-text">
            <input 
                type="text" 
                placeholder="Поиск"
                v-model="searchTextValue"
                @input="$emit('sortOrders', {filterType: 'textArea', value: searchTextValue})"
            />
        </div>
        <div class="form-date">
            <input 
                type="text" 
                placeholder="11.11.2021 - 11.11.2021"
                v-model="searchDateValue"
                @input="$emit('sortOrders', {filterType: 'dataArea', value: searchDateValue})"
            />
        </div>
        <div class="daily-filters">
            <div class="daily-all daily_active">
                <a href="/"
                    @:click.prevent="$emit('sortOrders', {filterType: 'all'})"
                >Все заказы</a>
                <span>15</span>
            </div>
            <div class="daily-today">
                <a href="/"
                    @:click.prevent="$emit('sortOrders', {filterType: 'today'})"
                >Заказы на сегодня</a>
                <span>15</span>
            </div>
            <div class="daily-tomorrow">
                <a href="/"
                    @:click.prevent="$emit('sortOrders', {filterType: 'tomorrow'})"
                >Заказы на завтра</a>
                <span>15</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                searchTextValue: '',
                searchDateValue: ''
            }
        },
        methods: {
            
        }
    }
</script>

<style>
    @import '../styles/FilterForm.css';
</style>