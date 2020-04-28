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
  // font-size: 0.1em;
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
  // font-family: Avenir, Helvetica, Arial, sans-serif;
  // color: #2c3e50;
  // margin-top: 60px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
