<template>
    <div class="filter-form">
        <div class="form-text">
            <input 
                type="text" 
                placeholder="Поиск"
                v-model="searchTextValue"
                @input="$emit('sortOrders', setTextValue(searchTextValue))"
            />
        </div>
        <div class="form-date">
            <input 
                type="text" 
                placeholder="11.11.2021 - 11.11.2021"
                v-model="searchDateValue"
                @input="$emit('sortOrders', setDateValue(searchDateValue))"
            />
        </div>
        <div class="daily-filters">
            <div class="daily-all" 
                :class="{daily_active: this.filters[2].value === 'all'}">
                <a href="/"
                    @click.prevent="$emit('sortOrders', setDayValue('all'))"
                >Все заказы</a>
                <span>{{totalCount || 0}}</span>
            </div>
            <div class="daily-today" 
                :class="{daily_active: this.filters[2].value === 'today'}"   
            >
                <a href="/"
                    @click.prevent="$emit('sortOrders', setDayValue('today'))"
                >Заказы на сегодня</a>
                <span>{{todayCount || 0}}</span>
            </div>
            <div class="daily-tomorrow"
                :class="{daily_active: this.filters[2].value === 'tomorrow'}"
            >
                <a href="/"
                    @click.prevent="$emit('sortOrders', setDayValue('tomorrow'))"
                >Заказы на завтра</a>
                <span>{{tomorrowCount || 0}}</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            totalCount: {
                type: Number,
            },
            todayCount: {
                type: Number,
            },
            tomorrowCount: {
                type: Number,
            }
        },
        data() {
            return {
                filters: [
                    {filter: 'textArea', value: ''},
                    {filter: 'dataArea', value: ''},
                    {filter: 'day', value: 'all'},
                ],
                searchTextValue: '',
                searchDateValue: ''
            }
        },
        methods: {
            setTextValue(value) {
                this.filters[0].value = value
                return this.filters 
            },
            setDateValue(value) {
                this.filters[1].value = value
                return this.filters 
            },
            setDayValue(value) {
                this.filters[2].value = value
                return this.filters 
            }
        }
    }
</script>

<style>
    @import '../styles/FilterForm.css';
</style>