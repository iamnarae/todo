<template>
    <section>
        <transition-group name="list" tag="ul">
            <li v-for="(todoItem, index) in propsdata" :key="todoItem">
                <span class="icon"></span>
                {{todoItem}}
                <span class="del" v-on:click="removeList(todoItem, index)">-</span>
            </li>
        </transition-group>
    </section>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
        removeList(todoItem, index) {
           this.$emit('remove', todoItem, index);
        }
    }
}
</script>

<style lang="scss">
.list-item {display:inline-block; margin-right:10px;}
.list-move {transition:transform .5s}
.list-enter-active, .list-leave-active {transition:all .5s}
.list-enter, .list-leave-to {opacity:0; transform:translateY(-30px)}
ul {list-style:none; padding:10px; 
    li {position:relative; height:40px; padding:10px 10px 10px 32px; margin-bottom:10px; border-radius:5px; line-height:20px; background:#fff;
        .icon {position:absolute; left:10px; top:10px; width:15px; height:16px; background:url(/images/common/ico_check.png) no-repeat 50% 50%;}
        .del {position:absolute; right:10px; top:10px; width:20px; height:20px; border:1px solid #740202; vertical-align:middle; text-align:center; line-height:16px; font-size:20px; font-weight:bold; color:#740202;}
    }
}

</style>
