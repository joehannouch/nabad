<template>
    <!-- <header class="header">
        <h1>Blood Requests</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header> -->

    <b-navbar toggleable="lg" type="dark" variant="danger" text-variant="white">
        
    <b-navbar-brand href="#">Blood Requests</b-navbar-brand>
    <!-- https://icc.edu/calendar/files/featured-image-red-cross-blood-drive.jpg -->
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
     

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
          
           <b-navbar-nav>
               <b-nav-item href="#" v-scroll-to="{el:'#requestcontainer', offest: -100}">Request Blood</b-nav-item>
               <b-nav-item href="#" v-scroll-to="{el:'#bloodsupplyrow', offest: -100}">Bank Supply</b-nav-item>
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

/* .header a{
    color: #fff;
    padding-right: 5px;
}


.router-link-exact-active{
    color:green;
} */
</style>