<script setup>
import { RouterView } from "vue-router";
import Header from "@/layout/Header.vue";
import Footer from "@/layout/Footer.vue";
</script>
<template>
  <Header></Header>
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
