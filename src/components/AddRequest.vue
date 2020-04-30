<template>
  <!-- <div>
      <form @submit="addBloodRequest">
          <input type="text" v-model="name" name="name" placeholder="Add Blood Request...">

          <input type="submit" value="Submit" class="btn">
      </form>

      <div> -->
<div id="requestform">
    
    <b-form @submit="onSubmit" @reset="onReset" class="requestform">
      <b-form-group id="input-group-1" label="Blood Type" label-for="input-1">
      <b-form-select
          id="input-1"
          v-model="form.bloodtypes"
          :options="bloodtypes"
          required
        ></b-form-select>
      </b-form-group>

        <b-form-group id="input-group-3" label="Blood Units" label-for="input-3">
      <b-form-select
          id="input-31"
          v-model="defaultbloodunits"
          :options="units"
          required
        ></b-form-select>
      </b-form-group>

        <b-form-group id="input-group-5" label="Area" label-for="input-5">
        <b-form-input
          id="input-5"
          v-model="form.area"
          required
          placeholder="Enter Area"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-4" label="Patient's Name:" label-for="input-4">
        <b-form-input
          id="input-4"
          v-model="form.patientname"
          
          placeholder="Enter patient's name (optional)"
        ></b-form-input>
      </b-form-group>

        <b-form-group id="input-group-2" label="Details" label-for="input-2">
        <b-form-input
            id="input-2"
            v-model="form.details"
            
            placeholder="Details (optional)"
        ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-7" label="Phone" label-for="input-7">
        <b-form-input
            id="input-7"
            v-model="form.phone"
            required
            placeholder="Phone Number"
        ></b-form-input>
        </b-form-group>

      <b-button type="submit" variant="primary" class="btn-block">Submit</b-button>
      <b-button type="reset" variant="danger" class="btn-block">Reset</b-button>
    </b-form>

  </div>

</template>

<script>

import { v4 as uuidv4 } from 'uuid';

export default {
    name: "AddRequest",
    data(){
        return{
        form: {
        
            patientname: '',
            details: '',
            bloodtypes: null,
            bloodunits: '3',
            area: '',
            phone: '',
        },
      
        show: true,
        bloodtypes: [{ text: 'Select Blood Type', value: null }, 'O-', 'O+', 'A-', 'A+', 'B-', 'B+', 'AB-','AB+'],
        defaultbloodunits: '3',
        units: [{ text: 'Select Units', value: null }, '1', '2', '3', '4', '5+'],
             
        }
    },
    methods:{
    onSubmit(evt) {
        evt.preventDefault()
            const newBloodRequest = {
                id: uuidv4(),
                type: 1,
                bloodtype: this.form.bloodtypes,
                bloodunits: this.defaultbloodunits,
                area: this.form.area,
                phone: this.form.phone,
                name: this.form.patientname,
                details: this.form.details,
                fulfilled: true,
                active: true
            }

            this.$emit('add-request', newBloodRequest);
      },
      onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.patientname = ''
        this.form.bloodtypes = ''
        this.form.units = ''
        this.form.details = ''
        this.form.area = ''
        this.form.phone = ''

        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      },
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
#requestform{
  padding: 40px;
}
.requestform{
  text-align: left;
}
</style>