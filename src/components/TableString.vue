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
            {{ order.Date }}
        </td>
        <td>
            {{ order.Weight }}
        </td>
        <td>
            {{ order.Type }}
        </td>
        <td>
            {{ order.OrderNum }}
        </td>
        <td>
            <OrderPath 
                v-if="order.accepted"
                v-bind:path="{A: order.PointA , B: order.PointB}"
            />
        </td>
        <td >
            <div class="executor-note">
                {{ order.Executor }}
                <img v-if="order.Executor === 'Идет подбор исполнителя' && order.accepted" src="../img/process-icon.png"/>
                <img v-else-if="order.accepted" src="../img/cp-icon.png"/>
            </div>
        </td>
        <td>
            <img v-if="order.GPS && order.accepted" src="../img/track-icon.png"/>
            <img v-if="!order.GPS && order.accepted" src="../img/location-icon.png"/>
        </td>
        <td>
            <img v-if="order.Documents && order.accepted" src="../img/file-icon.png"/>
            <img v-if="!order.Documents && order.accepted" src="../img/no-file-icon.png"/>
        </td>
        <td>
            {{ order.Cost }} 
            <span v-if="order.Cost">₽</span>
        </td>
        <td>
            {{ order.Payment }}
        </td>
    </tr>
</template>

<script>
    import OrderState from './OrderState.vue'
    import OrderPath from './OrderPath.vue'

    export default {
        components: {
            OrderState, OrderPath
        },
        props: {
            order: {
                type: Object,
                required: true
            }
        }
    }
</script>