<template>
    <!-- <div class="request-item" :class="{'is-fulfilled' : request.fulfilled}">
       <p>
           <input type="checkbox" v-on:change="markFulfilled">
           {{request.name}}
            <button class="del" @click="$emit('delete-request', request.id)">x</button>
       </p>
    </div> -->

    <div>
        <b-card no-body class="mb-1">
        <b-card-header header-tag="header" class="p-1" role="tab">
            <b-button block href="#" v-b-toggle="request.id" variant="info">{{request.name}}</b-button>
        </b-card-header>
        <b-collapse :id="request.id" accordion="my-accordion" role="tabpanel">
            <b-card-body>
            <b-card-text>{{ request.details }}</b-card-text>
            </b-card-body>
        </b-collapse>
        </b-card>
  </div>
</template>

<script>

export default{
    name:"Bloodrequest",
    props: ["request"],
    methods:{
        markFulfilled(){
            this.request.fulfilled = !this.request.fulfilled
        }
    }
}

</script>

<style scoped>
    .request-item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-fulfilled{
        text-decoration: line-through;
    }

    .del{
        background: #ff0000;
        color: #fff;
        border:none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float:right;
    }
</style>