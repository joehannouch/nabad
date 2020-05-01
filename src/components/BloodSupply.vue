<template>
  <div>
    <h3>Red Cross Local Blood Bank Supply</h3>
    <div v-for="bar in bars" class="row mb-3 bloodsupplyrow" v-bind:key="bar.varient">
      <div class="col-sm-2">
        <b-badge class="bloodtypebadge">{{ bar.type }} </b-badge>
      </div>
      <div class="col-sm-10 pt-1">
        <b-progress>
          <b-progress-bar
            class="progress-bar-low"
            :variant="bar.variant"
            :value="bar.value"
            :key="bar.variant"
          ></b-progress-bar>
        </b-progress>

        <!-- <b-progress :value="bar.value" :variant="bar.variant" :key="bar.variant"></b-progress> -->
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  data() {
    return {
      bars: [
        { variant: "warning", type: "A+", value: 25 },
        { variant: "warning", type: "A-", value: 50 },
        { variant: "warning", type: "B+", value: 75 },
        { variant: "danger", type: "B-", value: 10 },
        { variant: "danger", type: "AB+", value: 5 },
        { variant: "warning", type: "AB-", value: 60 },
        { variant: "warning", type: "O+", value: 20 },
        { variant: "warning", type: "O-", value: 30 }
      ]
    };
  }
};
</script>

<style>
.progress-bar {
  background-color: #df0101;
}
.progress-bar-low {
  background-color: #cdcdcd;
}
.progress {
  height: 2rem;
}
.bloodsupplyrow {
  height: 30px;
}
.bloodtypebadge {
  width: 54px;
  height: 35px;
  font-size: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  background-color: #df0101;
}
.progress-bar-vertical {
  width: 20px;
  min-height: 100px;
  display: flex;
  align-items: flex-end;
  margin-right: 20px;
  float: left;
}

.progress-bar-vertical .progress-bar-v {
  width: 100%;
  height: 0;
  -webkit-transition: height 0.6s ease;
  -o-transition: height 0.6s ease;
  transition: height 0.6s ease;
}
</style>