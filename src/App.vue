<template>
  <div class="app-container">
    <NavBar :logo="logo_src" :alt="app_name"/>
    <div class="main-content">
      <transition name="zoom-fade">
        <router-view :key="$route.fullPath"/>
    </transition>
    </div>
    <Footer/>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import Footer from './components/Footer.vue'

export default{
  components:{
    NavBar, 
    Footer
  },
  data(){
    return{
      logo_src:"/img/logo.png",
      app_name:"Make Your Burger"
    }
  }
}
</script>

<style>
*{
  font-family: Arial, Helvetica, sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.main-content {
  flex: 1; /* Ocupa o espaço restante, empurrando o footer para baixo */
}

h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}

/* Efeito de zoom */
.zoom-fade-enter-active, .zoom-fade-leave-active {
  transition: transform 0.5s ease, opacity 0.5s ease;
}
.zoom-fade-enter, .zoom-fade-leave-to /* .zoom-fade-leave-active em <2.1.8 */ {
  transform: scale(0.9);
  opacity: 0;
}
</style>
