<script>
import HelloWorld from "./components/HelloWorld.vue";
import DynamicRendering from "./components/DynamicRendering.vue"
const routes = {
  "/HelloWorld": HelloWorld,
  "/DynamicRendering":DynamicRendering
};

const links = [
  ["#/HelloWorld", "Hello World"],
  ["#/DynamicRendering", "Dynamic Rendering"]
];

export default {
  data() {
    return {
      links,
      currentPath: window.location.hash,
    };
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || "/"] || null;
    },
  },
  mounted() {
    window.addEventListener("hashchange", () => {
      this.currentPath = window.location.hash;
    });
  },
};
</script>

<template>
  <div  class="side">
    <ul class="none-list-stlye">
      <li v-for="[link, value] in links"><a :href="link">{{value}}</a></li>
    </ul>
  </div>
  
<div class="main">
  <component :is="currentView" />
</div>
  
</template>

<style scoped>
  .side{
    width: 25%;
    display: inline-block;
    vertical-align: top;
  }
  .main{
    width: 75%;
    display: inline-block;
  }
  .none-list-stlye{
    list-style-type: none;
  }
</style>
