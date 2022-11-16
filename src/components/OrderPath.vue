<template>
    <span class="order-path">
        <span>
            {{path.A}}
        </span>
        <img src="../img/arrow-icon.png" />
        <span>
            {{path.B}}
        </span>
    </span>
</template>

<script>
    export default {
        props: {
            path: {
                type: Object,
            }
        }
    }
</script>
