<template>
    <div class="request-item" :class="{'is-fulfilled' : request.fulfilled}">
       <p>
           <input type="checkbox" v-on:change="markFulfilled">
           {{request.name}}
            <button class="del" @click="$emit('delete-request', request.id)">x</button>
       </p>
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