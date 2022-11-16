<template>
    <div class="order-state"
        :class="[
            order.accepted === false ? 'state_unaccepted' : null,
            (order.accepted === true && order.state === 'Новый') ? 'state_new' : null,
            order.state === 'В работе' ? 'state_work' : null,
            order.state === 'Отказ' ? 'state_reject' : null,
            order.state === 'Отменён' ? 'state_cancell' : null,
            order.state === 'Доставлен' ? 'state_completed' : null
        ]"
    >
        {{ order.state }}
    </div>
</template>

<script>
    export default {
        props: {
            order: {
                type: Object,
            }
        },
    }
</script>

<style>
    @import url('../styles/OrderState.css');
</style>