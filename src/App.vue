<template>
  <div id="app">
    <nav>
      <div class="logo"><router-link to="/"><b>Useless App</b></router-link></div>
      <ul class="nav-links" :class="{'nav-active': showMenu}">
        <li>
          <router-link to="/about">About</router-link>
        </li>
        <li>
          <router-link to="/form">Contrived Form</router-link>
        </li>
      </ul>
      <div class="hamburger" @click="showMenu = !showMenu" :class="{'toggle': showMenu}">
        <div class="line1"></div>
        <div class="line2"></div>
        <div class="line3"></div>
      </div>
    </nav>
    <router-view/>
  </div>
</template>
<script>
  export default {
    name: "App",
    data: function () {
      return {
        showMenu: false
      }
    }
  }
</script>
<style>
  @import url('https://fonts.googleapis.com/css2?family=PT+Sans&display=swap');

  * {
    padding: 0;
    margin: 0;
  }
  #app {
    font-family: 'PT Sans', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }

  form label{
    font-size: 12px;
  }

  nav {
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 15px;
    background: #5555ee;
    color: white;
    
  }

  nav a, a:hover {
    color: white;
    text-decoration: none;
  }

  nav li{
    list-style: none;
  }

  .logo {
    font-size: 25px;
    flex: 3 1 auto;
  }

  .logo a{
    color: white !important;
  }

  .nav-links{
    display: flex;
    width: 35%;
    justify-content: space-around;  
    margin-bottom: 0;
  }

  .hamburger{
    display: none;
  }

  .hamburger div {
    width: 25px;
    height: 3px;
    background-color: white;
    margin: 5px;
  }

  .modal-footer{
    justify-content: space-around !important;
    border: none;
  }

  .modal-header{
    justify-content: space-around !important;
    border: none;
  }
  .modal-header h5{
    font-weight: bold;
  }
  .modal-body{
    text-align: center;
    padding: 0;
  }

  @media screen and (max-width: 468px){
    body{
      overflow-x: hidden;
    }
    .nav-links{
      position: absolute;
      right: 0px;
      top: 7vh;
      height: 15vh;
      background-color: #5555ee;
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;
      transform: translateY(-150%);
      /* transition: transform 0.25s ease-in; */
    }

    .hamburger{
      display: block;
    }
    .nav-active{
      transform: translateY(5%);
    }
  }
  .toggle .line1{
    transform: rotate(-45deg) translate(-5px,6px);
  }
  .toggle .line2{
    opacity: 0;
  }
  .toggle .line3{
    transform: rotate(45deg) translate(-5px,-6px);
  }

  nav a.router-link-exact-active {
    color: #d5dad8;
  }
</style>
