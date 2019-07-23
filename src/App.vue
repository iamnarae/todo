<template>
  <div id="app">
    <Header></Header>
    <Field v-on:add="addList"></Field>
    <List :propsdata="todoItems" v-on:remove="removeList"></List>
    <Footer v-on:removeAll="clearAll"></Footer>
  </div>
</template>

<script>
import header from './components/header.vue'
import field from './components/field.vue'
import list from './components/list.vue'
import footer from './components/footer.vue'

export default {
  data() {
    return {
      todoItems: []
    }
  },
  components: {
    'Header': header,
    'Field': field,
    'List': list,
    'Footer': footer
  },  
  created() {
      if(localStorage.length > 0){
          for (var i=0; i<localStorage.length; i++){
            this.todoItems.push(localStorage.key(i))
          }
      }
  },
  methods: {
        addList(todoItem) {
          localStorage.setItem(todoItem, todoItem);
          this.todoItems.push(todoItem);
        },
        removeList(todoItem, index) {
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        },
        clearAll(){
          localStorage.clear();
          this.todoItems = [];
        }
    }
}
</script>
<style lang="scss">
body {background:#dadada;}
* {padding:0; margin:0; box-sizing:border-box;}
</style>
