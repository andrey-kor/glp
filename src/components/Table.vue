<template>
    <div class="table__holder">
        <table>
            <thead>
                <tr>
                    <th>Статус заказа</th>
                    <th>Дата подачи</th>
                    <th>Тоннаж</th>
                    <th>Вид ТС</th>
                    <th>Номер заказа</th>
                    <th>Маршрут</th>
                    <th>Исполнитель</th>
                    <th>GPS</th>
                    <th>Документы</th>
                    <th>Стоимость</th>
                    <th>Оплата</th>
                </tr>
            </thead>
            <tbody>
                <TableString 
                    v-for="order of orders"
                    v-bind:order="order"
                />
            </tbody>
        </table>
    </div>
</template>

<script>
    import TableString from '@/components/TableString.vue'

    export default {
        props: {
            orders: {
                type: Array,
                required: true
            }
        },
        components: {
            TableString
        }
    }
</script>

<style>
    @import url('../styles/Table.css');
</style>