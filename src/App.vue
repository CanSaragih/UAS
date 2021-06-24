<template>
  <div id="app">
    <div id="nav" class="bg-red-500">
      <router-link to="/datacovid" >COUNTRIES AFFECTED BY COVID 19 </router-link>
    </div>  
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Ghoust Outline;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  font-size: 60px;
  color: #2c3e50;

}

#nav a.router-link-exact-active {
  color: #ffffff;
}
</style>
