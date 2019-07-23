<template>
    <div class="form">
        <input type="text" v-model="newItem" placeholder="할일을 적으세요" v-on:keyup.enter="addList">
        <span class="add" v-on:click="addList">+</span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newItem: ''
        }
    },
    methods: {
        addList() {
            if(this.newItem !== ''){
                var value = this.newItem && this.newItem.trim();
                this.$emit('add', value);
                this.clearInput();
            }
        },
        clearInput() {
            this.newItem = '';
        }
    }
}
</script>

<style lang="scss">
.form {padding:20px 0; border-top:1px solid #919090; border-bottom:1px solid #919090; text-align:center;
    input[type=text] {display:inline-block; width:300px; height:40px; padding:0 10px; border:1px none; border-radius:5px 0 0 5px; line-height:38px; vertical-align:top; background:#fff;}
    .add {display:inline-block; width:40px; height:40px; border-radius:0 5px 5px 0; vertical-align:top; text-align:center; line-height:1em; font-weight:700; font-size:30px; color:#fff; background:linear-gradient(to right, #6478fb, #8763fb);}
}
</style>

