<template>
  <div id="app">
    <dices />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Dices from "./components/Dices.vue";

@Component({
  components: {
    Dices
  }
})
export default class App extends Vue {}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #2c3e50;
  color: rgba(255, 255, 255, 0.226);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
