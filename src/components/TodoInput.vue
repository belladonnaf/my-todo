<template>
  <div>
    <input v-model="todoItem" type="text">
    <button v-on:click="addItem"><i class="fas fa-plus-square"></i></button>
  </div>
       

</template>

<script>
export default {
    data:function(){
        return {
            todoItem: ''
        }
    },
    mounted: function(){
//        this.todoItem = 'hi';
    },
    methods:{
        addItem: function(){
            var value = this.todoItem;
            this.$emit('send',value);            
            this.todoItem = '';
        }
    }
}

</script>

<style>

</style>
