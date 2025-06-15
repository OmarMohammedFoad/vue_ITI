<script>
import Header from "./components/Header.vue"
import HomePage from "./components/HomePage.vue";
import Footer from "./components/Footer.vue";
import Aside from "./components/Aside.vue"

export default {
  components: {
    Header,
    HomePage,
    Footer,
    Aside
  }
}
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <Header />
    
    <div class="flex flex-1">
      <Aside class="w-64 flex-shrink-0" />
      <main class="flex-2 ">
        <router-view></router-view>
      </main>
    </div>
    
    <Footer />
  </div>
</template>

<style scoped>
/* Ensure proper scrolling behavior */
main {
  max-height: calc(100vh - 120px); /* Adjust based on header/footer height */
}
</style>