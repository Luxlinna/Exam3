<template>
  <div id="app">
    <div id="nav" class="p-3 ml-4">
      <div>
        <img src="@/assets/icons/logo.png" class="my-logo text-left">
      </div>
      <div class="text-right p-4">
        <router-link to="/" class="ml-5">Home</router-link> 
        <router-link to="/about" class="ml-5">About</router-link> 
        <router-link to="/contact" class="ml-5">Contact Us</router-link> 
      </div>
    </div>
    
    <router-view/>
    <div id="footer" class="p-4 text-center">
        <footer class="text-light p-4">
            <a href="https://lms.se.beetroot.academy/myCourses/lesson/ckhxhrznu61d60880bj0nj9ln" target="_blank" class="text-warning">Build This Pages</a> |
            <a href="https://app.slack.com/client/T019E5XNM4Y/D01GB3DGE9G" class="text-warning">Privacy Policy</a>
            <br>
            <small>&copy; 2021, Linna</small>
        </footer>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #2c3e50;
}

.my-logo {
  width: 50px;
  height: 50px;
} 

#footer {
        background-color: #2c3e50;
}

.full-height {
  min-height: 100vh;
}

#nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: nowrap; /* assumes you only want one row */
}

#nav a {
  font-weight: bold;
  color: #FFFFFF;
  font-size: 20px;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
