<template>
  <div id="app">
    <br />
    <v-textarea
      class="textbox"
      filled
      placeholder="type something..."
      rows="6"
      row-height="30"
      rounded
      background-color="#fddbc9"
      autofocus
      @keydown.enter="onEnter"
      @keyup.enter="onEnter"
    ></v-textarea>
    <!-- emit event manually. since 'enter' event do not transmit with no reason. -->
    <Keyboard></Keyboard>
    <v-system-bar color="#fddbc9" height="30" class="system-bar">
      <v-spacer></v-spacer>
      <v-btn
        tile
        small
        icon
        @click="openLink('https://twitter.com/sgiori8/status/1254552525677756416')"
      >
        <v-icon>mdi-pencil-ruler</v-icon>
      </v-btn>
      <v-divider vertical style="margin: 4px;"></v-divider>
      <v-btn tile small icon @click="openLink('https://github.com/aungKhantPaing/keyboard')">
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-system-bar>
  </div>
</template>

<script>
import Keyboard from '@/components/Keyboard.vue';

export default {
  name: 'App',
  components: {
    Keyboard,
  },
  data() {
    return { text: '' };
  },
  methods: {
    onEnter(event) {
      document.dispatchEvent(
        new KeyboardEvent(event.type, {
          keyCode: 13, // example values
          location: 0,
        }),
      );
    },
    openLink(link) {
      window.open(link);
    },
    // onTab() {
    //   this.text += '        ';
    // },
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

.system-bar {
  position: fixed;
  left: 0px;
  bottom: 0px;
  width: 100%;
}

#app {
  // font-family: Avenir, Helvetica, Arial, sans-serif;
  // color: #2c3e50;
  // margin-top: 60px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
