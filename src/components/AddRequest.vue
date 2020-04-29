<template>
  <div>
      <form @submit="addBloodRequest">
          <input type="text" v-model="name" name="name" placeholder="Add Blood Request...">

          <input type="submit" value="Submit" class="btn">
      </form>
  </div>
</template>

<script>

import { v4 as uuidv4 } from 'uuid';

export default {
    name: "AddRequest",
    data(){
        return{
            name: ''
        }
    },
    methods:{
        addBloodRequest(e){

            console.log("Add request");

            e.preventDefault();

            const newBloodRequest = {
                id: uuidv4(),
                name: this.name,
                fulfilled: false,
          
            }

            this.$emit('add-request', newBloodRequest);

            this.name = '';
        }
    }
}
</script>

<style>
    form{
        display: flex;
    }

    input[type="text"]{
        flex:10;
        padding:5px;
    }

    input[type="submit"]{
        flex:2;
    }
</style>