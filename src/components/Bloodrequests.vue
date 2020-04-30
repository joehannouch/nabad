<template>
    <div id="requestform">
        <div v-for="request in requests" v-bind:key="request.id">
            <RequestItem v-bind:request="request" v-on:delete-request="$emit('delete-request', request.id)"/>
        </div>
    </div>
</template>

<script>

import RequestItem from './RequestItem';

export default{
    name:"Bloodrequests",
    components: {
        RequestItem
    },
    props: ["requests"]
}

</script>

<style scoped>
#requestform{
  padding: 40px;
}
</style>