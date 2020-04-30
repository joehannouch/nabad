<template>
    <!-- <header class="header">
        <h1>Blood Requests</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header> -->

    <b-navbar toggleable="lg" type="dark" variant="primary">
    <b-navbar-brand href="#"><router-link to="/">Blood Requests</router-link></b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
     

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
          
           <b-navbar-nav>
               <b-nav-item href="#"><b-link :to="'/'">Home</b-link></b-nav-item>
               <b-nav-item href="#"><b-link :to="'/about'">About</b-link></b-nav-item>

               
               
            </b-navbar-nav>
       
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>

export default {
    name: "Header"
}
</script>

<style scoped>

.header {
   background: #DF0101;
   color: #fff;
   text-align: center;
   padding: 10px;
}

.header a{
    color: #fff;
    padding-right: 5px;
}

.bg-primary {
    background:#DF0101 !important;
}

.router-link-exact-active{
    color:green;
}
</style>