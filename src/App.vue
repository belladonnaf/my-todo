<template>
  <div>
    <todo-header></todo-header>
    <todo-input @send="addTodoItem"></todo-input>
    <todo-list :propsdata="todoItems" @delete="removeTodoItem"></todo-list>
<!--    <todo-footer @delete:all="removeAllTodoItem"></todo-footer>  /-->
    <todo-footer></todo-footer> 
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";
import { eventBus } from './utils/eventBus.js';

export default {

    data:function(){
        return {
            todoItems:[]
        }
    },
    methods:{

          addTodoItem: function(value) {

            console.log(value);
//            var value = this.todoItem;

            if(!value){
                value = 'xx';
            }
            console.log(jj);
//            console.log(jj.push(value));
            if( !localStorage.getItem('jj') ){
                var jj = [];
                jj.push(value);
            } else {
                var jj = JSON.parse(localStorage.getItem('jj'));
                jj.push(value);
            }
            localStorage.setItem('jj', JSON.stringify(jj) );
            this.todoItems.push(value);

          },        
          removeTodoItem:function(todoItem,index){
           var jj = JSON.parse(localStorage.getItem('jj'));
            this.todoItems.splice(index,1);
           jj.splice(index,1);
           localStorage.setItem('jj', JSON.stringify(jj) );
          },
          removeAllTodoItem:function(){
            localStorage.clear('jj');
            this.todoItems = [];
          }

//          removeItem: function(index){
//           var jj = JSON.parse(localStorage.getItem('jj'));
//            this.todoItems.splice(index,1);
//           jj.splice(index,1);
//           localStorage.setItem('jj', JSON.stringify(jj) );


    },
    components: {
      'todo-header': TodoHeader,
      'todo-input': TodoInput,
      'todo-list': TodoList,
      'todo-footer': TodoFooter
    },
    created(){

        var data = JSON.parse(localStorage.getItem("jj"));
        console.log(data);
        if(data){

            for ( var k in data){
                if(data[k]){
                    this.todoItems.push(data[k]);
                }
            }

        }
      var vm = this; // 이 this는 컴포넌트(38번)를 가리키고
      eventBus.$on('delete:all', function() {
        // this는 이벤트 버스의 컴포넌트 (40번)
        vm.removeAllTodoItem();
      });
  } 

}


</script>

<style>
</style>
