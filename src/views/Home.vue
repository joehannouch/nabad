<template>

<b-container class="bv-example-row">
  <b-row>
    <b-col>
      
      <div id="app">
        <AddRequest v-on:add-request="addRequest"/>
        <Bloodrequests v-bind:requests="requests" v-on:delete-request="deleteRequest"/>
      </div>

    </b-col>
   
  </b-row>
</b-container>

  
</template>

<script>
import Vue from 'vue'
import Bloodrequests from '../components/Bloodrequests';
import AddRequest from '../components/AddRequest';
import VueToast from 'vue-toast-notification';

import 'vue-toast-notification/dist/theme-default.css';


Vue.use(VueToast);

export default {
  
  name: 'Home',
  components: {
    Bloodrequests,
    AddRequest
  },
  data(){
    return {
      count: 0,

      requests:[
        {
          id:1,
          type: 1,
          bloodtype: "B+",
          bloodunits: 5,
          area: "Jounieh",
          phone: "+96170240062",
          name: "Michel Khoury",
          details: "Open Heart Surgery, AUH",
          fulfilled: true,
          active: true
        },
        {
          id:2,
          type: 1,
          bloodtype: "A-",
          bloodunits: 3,
          area: "Beirut",
          phone: "+96170240062",
          name: "Jean Khalil",
          details: "",
          fulfilled: false,
          active: true
        },
        {
          id:3,
          type: 1,
          bloodtype: "O-",
          bloodunits: 5,
          area: "Mansourieh",
          phone: "+96170240062",
          name: "Elie Mousallem",
          details: "",
          fulfilled: true,
          active: true
        },
        {
          id:4,
          type: 2,
          bloodtype: "AB+",
          bloodunits: 4,
          area: "Jbeil",
          phone: "+96170240062",
          name: "Salam Salloum",
          details: "",
          fulfilled: false,
          active: true
        }
      ]
    }
  },
  methods:{
    deleteRequest(id){
      this.requests = this.requests.filter(request => request.id !== id)
    },
    addRequest(newRequest){

      if(newRequest.name == ""){
         Vue.$toast.warning('Please fill are required fields',
        {
          position: 'top'
        })

        
      }else{
         if(this.count < 1){
          this.requests = [...this.requests, newRequest];
          Vue.$toast.open(
          {
            message: 'Blood Request Active',
            position: 'top'
          });


        this.count++;

      }else{

        Vue.$toast.error('You already have an active request',
        {
          position: 'top'
        })

         
      }
      }
     
      
    }
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn{
    display: inline-block;
    border:none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer
  }
  .btn:hover{
    background: #666;
  }
</style>
