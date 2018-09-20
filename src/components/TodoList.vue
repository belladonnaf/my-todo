<template>
  <div class="inputBox ">
    list
     <ul>
         <li v-for="(todoItem, index) in propsdata">{{todoItem}}<span class="removeBtn" v-on:click="removeItem(todoItem,index);"><i class="fas fa-trash-alt"></i></span></li>

     </ul>
  </div>
</template>

<script>
export default {
    props:['propsdata'],
    methods:{

        removeItem: function(todoItem,index){
//           var jj = JSON.parse(localStorage.getItem('jj'));
//            this.todoItems.splice(index,1);
//           jj.splice(index,1);
//           localStorage.setItem('jj', JSON.stringify(jj) );
            var deleteItem = { 
                'todoItem' : todoItem,
                'index':index
            }
            this.$emit('delete',todoItem,index);
        }
    
    }
}
</script>


<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>