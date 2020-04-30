<template>
  <!-- <div class="request-item" :class="{'is-fulfilled' : request.fulfilled}">
       <p>
           <input type="checkbox" v-on:change="markFulfilled">
           {{request.name}}
            <button class="del" @click="$emit('delete-request', request.id)">x</button>
       </p>
  </div>-->

  <div>
    <b-card no-body class="mb-1">
      <b-card-header header-tag="header" role="tab">
        <b-button class="requestButton" block href="#" v-b-toggle="request.id" variant="info">
          <div class="requestArea">{{request.area}}</div>

          <div class="requestType">
            {{request.bloodtype}}
            <span class="bloodunits">
              <font-awesome-icon class="dropicon" :class="{'dropiconred' : request.bloodunits >= 1}" icon="tint" />
              <font-awesome-icon class="dropicon" :class="{'dropiconred' : request.bloodunits >= 2}" icon="tint" />
              <font-awesome-icon class="dropicon" :class="{'dropiconred' : request.bloodunits >= 3}" icon="tint" />
              <font-awesome-icon class="dropicon" :class="{'dropiconred' : request.bloodunits >= 4}" icon="tint" />
              <font-awesome-icon class="dropicon" :class="{'dropiconred' : request.bloodunits >= 5}" icon="tint" />
            </span>
          </div>
        </b-button>
      </b-card-header>

      <b-collapse :id="request.id" accordion="my-accordion" role="tabpanel" class="requestBody">
        <b-card-body>
          <b-card-text>{{ request.details }}</b-card-text>
        </b-card-body>
      </b-collapse>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "Bloodrequest",
  props: ["request"],
  methods: {
    markFulfilled() {
      this.request.fulfilled = !this.request.fulfilled;
    }
  }
};
</script>

<style scoped>
.request-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-fulfilled {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
.collapsed > .when-opened,
:not(.collapsed) > .when-closed {
  display: none;
}

.requestButton {
  height: 80px;
  border-radius: 0px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: black;
  background-color: white;
  border: none;
  padding-left: 50px;
  padding-right: 10px;
}

.requestArea {
  font-size: 22px;
}
.requestType {
  font-size: 25px;
  font-weight: bold;
  text-align: center;
  width: 100px;
}

.requestBody {
  position: relative;
  top: -10px;
}
.card {
  border: none;
}
.card-header {
  padding: 0px;
}

.btn-info:not(:disabled):not(.disabled):active {
  background-color: #fff;
  color: black;
}
.requestButton:hover {
  background-color: #ccc;
}

.bloodunits {
  display: block;
  font-size: 13px;
}

.dropicon{
 margin:1px;   
 color: #ddd;
}

.dropiconred{
 margin:1px;   
 color: #ff0000;
}
</style>