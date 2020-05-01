<template>

<b-container>

  <b-row class="mt-5">
    <b-col >
    <MainJumbo/>
    </b-col>
  </b-row>
  <b-row class="mt-5">
    <b-col >
      <BloodSupply/>
    </b-col>
  </b-row>
  <b-row class="mt-5">
   
    <b-col>
      <div id="app">
        <h3>Live Requests</h3>
        <p>Blood requests around you</p>
        <div role="tablist" id="requestsList">
        <Bloodrequests v-bind:requests="requests" v-on:delete-request="deleteRequest"/>
        </div>
      </div>

    </b-col>

     <b-col>

       <h3>Request Blood</h3>
       <p>Please fill the form below to complete your request</p>

        <AddRequest v-on:add-request="addRequest"/>
    </b-col>
   
  </b-row>
</b-container>

  
</template>

<script>
import Vue from 'vue'
import Bloodrequests from '../components/Bloodrequests';
import AddRequest from '../components/AddRequest';
import BloodSupply from '../components/BloodSupply';
import MainJumbo from '../components/MainJumbo';

import VueToast from 'vue-toast-notification';

import 'vue-toast-notification/dist/theme-default.css';


Vue.use(VueToast);

export default {
  
  name: 'Home',
  components: {
    Bloodrequests,
    AddRequest,
    BloodSupply,
    MainJumbo
  },
  data(){
    return {
      count: 0,

      requests:[
        {
          id:'1',
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
          id:'2',
          type: 1,
          bloodtype: "A-",
          bloodunits: 2,
          area: "Beirut",
          phone: "+96170240062",
          name: "Jean Khalil",
          details: "",
          fulfilled: false,
          active: true
        },
        {
          id:'3',
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
          id:'4',
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
            message: 'Blood Request submitted, \r\n It will automatically expire in 3 days',
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
  .bloodsupply{
    width: 50%;
  }

  #requestsList{
    background-color: #f2f6f9;
  }

  
</style>
