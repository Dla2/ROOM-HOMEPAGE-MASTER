<template>
    <div class="navbar-wrapper">

        <div class="mobile-navbar-wrapper">
            <Transition name="fade" mode="out-in">
                <div class="mobile-navbar" v-if="navbarActive" >
                    <img src="../assets/icon-hamburger.svg" alt="mobile hamburger button icon" @click="navbarActive = !navbarActive">
                    <h1>room</h1>
                </div>
    
                <div class="mobile-navbar-active" v-else>
                    <img src="../assets/icon-close.svg" alt="close mobile hamburger button icon" @click="navbarActive = !navbarActive">
                    <ul>
                        <li v-for="(link, index) in links" :key="index"><a href="">{{ link }}</a></li>
                    </ul>
                </div>
            </Transition>
        </div>

        <div class="desktop-navbar">
            <h1>room</h1>
            <ul>
                <li v-for="(link, index) in links" :key="index"><a href="">{{ link }}</a></li>
            </ul>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
// array containing navbar link
const links = ['home', 'shop', 'about', 'contact']
// navbar active state
const navbarActive = ref(true)

</script>

<style scoped>
 .navbar-wrapper .mobile-navbar-wrapper .mobile-navbar {
    display: flex;
    align-items: center;
    gap: 7rem;
    padding: 3rem 1.5rem;
    min-width: 375px;
 }
 .navbar-wrapper .desktop-navbar {
    display: none;
    gap: 3.5rem;
    align-items: center;
    padding: 4rem 4rem 0rem;
 }
 .navbar-wrapper .mobile-navbar-wrapper .mobile-navbar h1, .navbar-wrapper .desktop-navbar h1 {
    color: var(--White);
 }
 .navbar-wrapper .mobile-navbar-wrapper .mobile-navbar-active {
    display: flex;
    padding: 3rem 1.5rem;
    background-color: var(--White);
    min-width: 375px;
    align-items: center;
    justify-content: space-between;
 }
 .navbar-wrapper .mobile-navbar-wrapper .mobile-navbar-active ul, .navbar-wrapper .desktop-navbar ul {
    display: flex;
    list-style-type: none;
    align-items: center;
    gap: 2rem;
    padding: 0;
 }
 .navbar-wrapper .desktop-navbar ul li a {
    text-decoration: none;
    color: var(--White);
    border-bottom: 4px transparent solid;
    transition: all 0.5s linear;
 }
 .navbar-wrapper .desktop-navbar ul li a:hover {
    border-bottom: 4px var(--White) solid;
 }
 .navbar-wrapper .mobile-navbar-wrapper .mobile-navbar-active ul a {
    text-decoration: none;
    color: var(--Black);
 } 

.fade-enter-active,.fade-leave-active {
  transition: opacity 0.5s ease, transform 0.5s ease;
}


.fade-enter-from,.fade-leave-to {
  opacity: 0;
  transform: translateX(-20px);
}

@media screen and (min-width: 700px) {
    .navbar-wrapper .mobile-navbar-wrapper {
        display: none;
    }
    .navbar-wrapper .desktop-navbar {
        display: flex;
    }
}
</style>