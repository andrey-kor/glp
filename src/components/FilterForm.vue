<template>
    <div class="filter-form">
        <div class="form-text">
            <input type="text" placeholder="Поиск"/>
        </div>
        <div class="form-date">
            <input type="text" placeholder="11.11.2021 - 11.11.2021"/>
        </div>
        <div class="daily-filters">
            <div class="daily-all daily_active">
                <a>Все заказы</a>
                <span>15</span>
            </div>
            <div class="daily-today">
                <a>Заказы на сегодня</a>
                <span>15</span>
            </div>
            <div class="daily-tomorrow">
                <a>Заказы на завтра</a>
                <span>15</span>
            </div>
        </div>
    </div>
</template>

<style>
    @import '../styles/FilterForm.css';
</style>