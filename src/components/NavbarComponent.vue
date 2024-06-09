<template>
  <header :class="{ 'scrolled-nav': scrollPosition }">
    <nav>
      <router-link to="/">
        <div class="nav-logo">
          <img :src="Geoh" alt="logo" />
        </div>
      </router-link>
      <div class="ticket">
        <img :src="Ticket" alt="ticket" />
      </div>
      <div class="search-icon">
        <i class="material-icons">search</i>
      </div>
      <div
        :class="{ open: isOpen }"
        @click="toggleMenu"
        class="nav-icon"
        id="nav-icon3"
      >
        <!-- Add class 'burger-menu' if mobile is true -->
        <span></span>
        <span></span>
        <span></span>
        <span></span>
      </div>
      <ul class="dropdown-menu" v-if="isOpen">
        <router-link to="/signup">
          <li>Registrer</li>
        </router-link>
        <router-link to="/signin">
          <li>Log ind</li>
        </router-link>
        <router-link to="/pointshop">
          <li>Point Shop</li>
        </router-link>
        <router-link to="/skattejagt">
          <li>Skattejagt</li>
        </router-link>
        <li @click="signOut">Log ud</li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref } from "vue";

const isOpen = ref(false);
const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};

import Ticket from "../assets/icons/billet.png";
import Geoh from "../assets/icons/Geoh.png";

const scrollPosition = ref(false);
const mobile = ref(window.innerWidth < 768);

// Update mobile value when window size changes
window.addEventListener("resize", () => {
  mobile.value = window.innerWidth < 768;
});
</script>

<style scoped>
nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  position: relative;
  align-items: center;
  background-color: var(--primary-green);
  padding: 10px;
  height: 70px;
}

.nav-logo {
  display: flex;
  align-items: center;
}

.nav-logo img {
  max-width: 100%;
  max-height: 100%;
}

.ticket {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fae284;
  height: 70px; /* Juster højden efter behov */
  width: 35%; /* Juster bredden efter behov */
  margin-left: 10px;
  margin-right: 10px;
}

.ticket img {
  max-width: 100%;
  max-height: 100%;
}

.search-icon {
  display: flex;
  width: 70px;
  height: 70px;
  justify-content: center;
  align-items: center;
  .material-icons {
    color: #fff;
    font-size: 45px;
  }
}

.search-icon img {
  width: 30px;
  height: 30px;
}

.nav-icon {
  width: 45px;
  height: 35px;
  position: relative;
  margin: 0 20px;
  cursor: pointer;
}

.nav-icon span {
  display: block;
  position: absolute;
  height: 7px;
  width: 100%;
  background: #fff;
  border-radius: 7px;
  opacity: 1;
  left: 0;
  transition: 0.25s ease-in-out;
}

/* Dropdown menu */
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  background-color: var(--background-color);
  width: 100%;
  padding: 5px 0;
  display: flex;
  flex-direction: column;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  z-index: 9999;
}

.dropdown-menu li {
  padding: 10px 20px;
  transition: background-color 0.3s;
  list-style: none;
  cursor: pointer;
  font-weight: 600;
  font-size: 18px;
  font-family: "Open Sans", sans-serif;
  text-transform: uppercase;
}

.dropdown-menu li:hover {
  background-color: #e0e0e0;
}

.open span:nth-child(1) {
  top: 18px;
  width: 0%;
  left: 50%;
}

.open span:nth-child(2) {
  transform: rotate(45deg);
}

.open span:nth-child(3) {
  transform: rotate(-45deg);
}

.open span:nth-child(4) {
  top: 18px;
  width: 0%;
  left: 50%;
}

.scrolled-nav {
  background-color: var(--primary-dark-green);
}
</style>
