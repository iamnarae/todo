<template>
    <footer>
        <span class="clearAll" @click="clear">Clear All</span>
    </footer>
</template>

<script>
export default {
    data() {

    },
    methods: {
        clear() {
            this.$emit('removeAll')
        }
    }
}
</script>

<style lang="scss">
footer {padding-bottom:50px; text-align:center;
    .clearAll {display:inline-block; height:40px; padding:0 10px; border-radius:5px; line-height:40px; font-size:16px; font-weight:bold; color:rgb(187, 100, 2); background:#fff;}
}
</style>
