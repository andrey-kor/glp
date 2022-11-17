<template>
    <span class="pay-state"
        :class="[
            order.payment === 'Не оплачен' ? 'payment_no' : null,
            order.payment === 'Счет выставлен' ? 'payment_bill' : null,
            order.payment === 'Оплачен' ? 'payment_completed' : null
        ]"
    >
        {{ order.payment }}
    </span>
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
    @import url('../styles/PayState.css');
</style>