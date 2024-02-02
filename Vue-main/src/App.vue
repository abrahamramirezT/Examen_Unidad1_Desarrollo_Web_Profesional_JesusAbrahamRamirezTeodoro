<script setup>
// import HelloWorld from './components/HelloWorld.vue'
import NavBar from "./components/NavBar.vue";

</script>

<template>
  <div id="app">
    <header>
      <NavBar></NavBar>
    </header>
    <main>
      
      <div class="content">
        <router-view></router-view>
      </div>
    </main>
  </div>
</template>

<style scoped>
#sidebar {
  position: absolute;
  z-index: 0;
}

.content {
  margin-left: 260px;
  margin-top: 56px;
}
</style>
