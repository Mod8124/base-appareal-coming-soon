<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
   <Img>
   <template v-slot:logoMobile>
     <img src="./assets/images/logo.svg" alt="logo">
   </template>
    <template v-slot:img>
      <img src="./assets/images/hero-mobile.jpg" alt="actres" class="mobile">
      <img src="./assets/images/hero-desktop.jpg" alt="actres" class="desktop">
    </template>
   </Img>
     <Cta>
        <template v-slot:logoLg>
     <img src="./assets/images/logo.svg" alt="logo">
   </template>
    <template v-slot:title>
       <span>  We're</span> coming soon
    </template>

      <template v-slot:info>
         Hello fellow shoppers! We're currently building our new fashion store. 
        Add your email below to stay up-to-date with announcements and our launch deals.
    </template>

     </Cta>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Img from './components/Img.vue'
import Cta from './components/Cta.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Img,
    Cta
  }
 
}
</script>

<style>
@import '../assets/css/app.css';


.mobile {
  display: block;
}

.desktop {
  display: none;
}

@media screen and (min-width:800px) {
  .cta {
  background-image: url('./assets/images/bg-pattern-desktop.svg');
  background-size: contain;
}

  .desktop {
    display: block;
  }

  .mobile {
    display: none;
  }
}

</style>
