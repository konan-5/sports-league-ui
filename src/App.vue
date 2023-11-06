<script setup>
import { RouterView } from "vue-router";
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";
</script>
<template>
  <Navbar></Navbar>
  <RouterView />
  <Footer></Footer>
</template>

<style>
@import "./index.css";

.welcomeMessage {
  margin: 120px auto;
  width: 50%;
  text-align: left;
  font-size: 24px;
}
</style>
