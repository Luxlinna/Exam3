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
    <div id="footer" class="p-2 text-center">      
        <footer class="text-light p-4">
            <a href="https://lms.se.beetroot.academy/myCourses/lesson/ckhxhrznu61d60880bj0nj9ln" target="_blank" class="text-warning">Build This Pages</a> |
            <a href="https://app.slack.com/client/T019E5XNM4Y/D01GB3DGE9G" class="text-warning">Privacy Policy</a>
            <br>
            <small>&copy; 2021, Linna</small>
           <div class="my-icons mt-3">
              <a href="https://www.facebook.com" class="fa fa-facebook ml-4 p-2"></a>
              <a href="https://twitter.com" class="fa fa-twitter ml-4 p-2"></a>
              <a href="https://www.google.com" class="fa fa-google ml-4 p-2"></a>
              <a href="https://www.linkedin.com" class="fa fa-linkedin ml-4 p-2"></a>
              <a href="https://www.youtube.com" class="fa fa-youtube ml-4 p-2"></a>
           </div>
        </footer>
    </div>
  </div>
</template>

<style>
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css');

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

/* Start my icons and colors style */
.my-icons {
    display: flex;
    flex-direction: row;
    justify-content: center;
    flex-wrap: nowrap; /* assumes you only want one row */
  }
  
  .fa {  
      width: 30px;
      padding: 7px;
      font-size: 20px;
      text-align: center;
      text-decoration: none;
      margin: 2px 2px;
      color: white;
      border-radius: 50%; 
  }
  
  .fa:hover {
      opacity: 0.7;
  }
  
  .fa-facebook {
      background: #3B5998;
  }
  
  .fa-twitter {
      background: #55ACEE;
  }
  
  .fa-google {
      background: #dd4b39;
  }
  
  .fa-linkedin {
      background: #007bb5;
  }
  
  .fa-youtube {
      background: #bb0000;
  }
  /* End my icons and colors style */
</style>
