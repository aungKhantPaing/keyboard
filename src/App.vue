<template>
  <div id="app">
    <Keyboard></Keyboard>
  </div>
</template>

<script>
import Keyboard from '@/components/Keyboard.vue';
export default {
  name: 'App',
  components: {
    Keyboard,
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Varela&display=swap');

html,
body {
  font-family: 'Varela', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 0;
  height: auto;
  width: 100%;
  background: white;
  color: white;
}
#app {
  text-align: -webkit-center !important;
  // font-family: Avenir, Helvetica, Arial, sans-serif;
  // -webkit-font-smoothing: antialiased;
  // -moz-osx-font-smoothing: grayscale;
  // color: #2c3e50;
  // margin-top: 60px;
}
</style>
