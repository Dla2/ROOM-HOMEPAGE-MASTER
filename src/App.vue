<script setup>
import { ref } from 'vue';
// import for all components used in this project
import Navbar from './components/Navbar.vue';
import DiscoverInnovative from './components/DiscoverInnovative.vue';
import AvailableGlobal from './components/AvailableGlobal.vue';
import ManufacturedMaterials from './components/ManufacturedMaterials.vue'
import About from './components/About.vue';
// count variable
const count = ref(0);
// function used to add or change the count variable when a button is clicked
const addCount = () => {
  if (count.value == 2) {
    count.value = 0;
  } else {
    count.value = count.value + 1;
  }
}
// function used to subtract or cahnge the count variable when a button is clicked
const subCount = () => {
  if (count.value === 0) {
    count.value = 2;
  } else {
    count.value = count.value - 1;
  }
}

const goLeft = (n) => {
  if (n <= 0) {
    count.value = 2;
  } else {
    count.value = count.value - 1
  }
}

const goRight = (n) => {
  if (n >= 2) {
    count.value = 0
  } else {
    count.value = count.value + 1
  }
}
</script>

<template class="room-homepage-wrapper">
  <main>

    <header>
  
      <Transition mode="out-in" name="fade">
        <img  src="./assets/desktop-image-hero-1.jpg" alt="image showing two white chairs a desk and a bonsai tree set on the table in a grey coloured room" v-if="count == 0" class="desktop-img">
        <img  src="./assets/desktop-image-hero-2.jpg" alt="image showing three chairs coloured orange greyish green and beige in a dull coloured room" v-else-if="count == 1" class="desktop-img">
        <img  src="./assets/desktop-image-hero-3.jpg" alt="image showing an all black folding chair in a grey coloured room" v-else-if="count == 2" class="desktop-img">
      </Transition>
  
      <Transition name="fade" mode="out-in">
        <img src="./assets/mobile-image-hero-1.jpg" alt="image showing two white chairs a desk and a bonsai tree set on the table in a grey coloured room" v-if="count == 0" class="mobile-img">
        <img src="./assets/mobile-image-hero-2.jpg" alt="image showing three chairs coloured orange greyish green and beige in a dull coloured room" v-else-if="count == 1" class="mobile-img">
        <img src="./assets/mobile-image-hero-3.jpg" alt="image showing an all black folding chair in a grey coloured room" v-else-if="count == 2" class="mobile-img">
      </Transition>
  
      <Navbar class="navbar"/>
  
      <div class="change-btns">
        <button><img src="./assets/icon-angle-left.svg" alt="angle left/ go left button icon" @click="subCount"></button>
        <button><img src="./assets/icon-angle-right.svg" alt="angle right/ go right button icon" @click="addCount"></button>
      </div>
  
    </header>
  
    <Transition mode="out-in" name="fade">
  
      <DiscoverInnovative v-if="count == 0" :count="count" class="discover-innovative-component" @add-count="goRight"  @sub-count="goLeft"/>
      <AvailableGlobal v-else-if="count == 1" :count="count" class="available-global-component" @add-count="goRight"  @sub-count="goLeft"/>
      <ManufacturedMaterials v-else-if="count == 2" :count="count" class="manufactured-materials-component" @add-count="goRight"  @sub-count="goLeft"/>
  
    </Transition>
  
    <img src="./assets/image-about-dark.jpg" alt="image showcasing dark coloured furniture in a dark room " class="about-furniture-dark">
  
    <About  class="about-component"/>
  
    <img src="./assets/image-about-light.jpg" alt="image showcasing light coloured chaur in a very light room" class="about-furniture-light">
  </main>

</template>

<style scoped>
header {
  position: relative;
}
header .desktop-img {
  display: none;
}
header .navbar {
  top: 0;
  position: absolute;
}
header .change-btns {
  right: 0;
  bottom: 6px;
  position: absolute;
}
header .change-btns button{
  border: none;
  background-color: var(--Black);
  padding: 1.25rem 1.5rem;
  cursor: pointer;
}

img {
  max-width: 100%;
  max-height: 100%;
}

@media screen and (min-width: 375px) {
  header .desktop-img {
    display: block;
    align-self: center;
  }
  header .mobile-img {
    display: none;
  }
  header .change-btns {
    bottom: 0px;
  }
  .about-furniture-dark, .about-furniture-light {
    display: inline-flex;
    margin: 0 auto;
  }
}

@media screen and (min-width: 500px) {
    header .change-btns {
    display: none;
  }
  .about-furniture-dark, .about-furniture-light {
    display: block;
  }
}

@media screen and (min-width: 840px) {
  main {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: max-content max-content;
  }
  header {
    grid-column: 1/5;
    display: grid;
  }
  header .desktop-img {
    display: block;
    align-self: center;
  }
  header .mobile-img {
    display: none;
  }
  header .change-btns {
    display: none;
  }
  .discover-innovative-component, .available-global-component, .manufactured-materials-component {
    grid-column: 5/8;
  }
  .about-furniture-dark {
    grid-column: 1/3;
  }
  .about-component {
    grid-column: 3/6;
  }
  .about-furniture-light {
    grid-column: 6/8;
  }
}

.fade-enter-active,.fade-leave-active {
  transition: opacity 0.5s ease, transform 0.5s ease;
}


.fade-enter-from,.fade-leave-to {
  opacity: 0;
  transform: translateX(-20px);
}
</style>
