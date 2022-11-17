<template>
    <tr style="position:relative">
        <td>
            <OrderState v-bind:order="order"/>
        </td>
        <td>
            <div v-if="!order.accepted" class="processing-note">
                Ваша заявка находится в обработке у диспетчера скоро здесь появяться заказы 
                с назначенными исполнителями 
                <img src="../img/process-icon.png"/>
            </div>
            {{ order.date }}
        </td>
        <td>
            {{ order.weight }}
        </td>
        <td>
            {{ order.type }}
        </td>
        <td>
            {{ order.orderNum }}
        </td>
        <td>
            <OrderPath 
                v-if="order.accepted"
                v-bind:path="{A: order.pointA , B: order.pointB}"
            />
        </td>
        <td >
            <div class="executor-note">
                {{ order.executor }}
                <img v-if="order.executor === 'Идет подбор исполнителя' && order.accepted" src="../img/process-icon.png"/>
                <img v-else-if="order.accepted" src="../img/cp-icon.png"/>
            </div>
        </td>
        <td>
            <img v-if="order.gps && order.accepted" src="../img/track-icon.png"/>
            <img v-if="!order.gps && order.accepted" src="../img/location-icon.png"/>
        </td>
        <td>
            <img v-if="order.documents && order.accepted" src="../img/file-icon.png"/>
            <img v-if="!order.documents && order.accepted" src="../img/no-file-icon.png"/>
        </td>
        <td>
            {{ order.cost }} 
            <span v-if="order.cost">₽</span>
        </td>
        <td>
            <PayState v-bind:order="order"/>
        </td>
    </tr>
</template>

<script>
    import OrderState from './OrderState.vue'
    import OrderPath from './OrderPath.vue'
    import PayState from './PayState.vue'

    export default {
        components: {
            OrderState, OrderPath, PayState
        },
        props: {
            order: {
                type: Object,
                required: true
            }
        }
    }
</script>