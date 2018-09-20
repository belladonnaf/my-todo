<template>
  <div>
    <button @click="removeAll">Clear</button>
  </div>
</template>
    
<script>
import { eventBus } from '../utils/eventBus.js';
export default {


    methods:{
        removeAll: function(index){
            this.$emit('delete:all')
//           localStorage.clear('jj');

        }
    }    

}
</script>

<style>

</style>
