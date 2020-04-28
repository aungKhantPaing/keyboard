<template>
  <div class="container">
    <div class="key-container">
      <div class="row1">
        <span class="esc f-keys">
          <span>esc</span>
        </span>
        <span class="F1 f-keys">F1</span>
        <span class="F2 f-keys">F2</span>
        <span class="F3 f-keys">F3</span>
        <span class="F4 f-keys">F4</span>
        <span class="F5 f-keys">F5</span>
        <span class="F6 f-keys">F6</span>
        <span class="F7 f-keys">F7</span>
        <span class="F8 f-keys">F8</span>
        <span class="F9 f-keys">F9</span>
        <span class="F10 f-keys">F10</span>
        <span class="F11 f-keys">F11</span>
        <span class="F12 f-keys">F12</span>
        <span class="touchID f-keys"></span>
      </div>

      <div class="row2">
        <KeyCap label="`" side-label="~" />
        <KeyCap label="1" side-label="!" />
        <KeyCap label="2" side-label="@" />
        <KeyCap label="3" side-label="#" />
        <KeyCap label="4" side-label="$" />
        <KeyCap label="5" side-label="%" />
        <KeyCap label="6" side-label="^" />
        <KeyCap label="7" side-label="&amp;" />
        <KeyCap label="8" side-label="*" />
        <KeyCap label="9" side-label="(" />
        <KeyCap label="0" side-label=")" />
        <KeyCap label="-" side-label="_" />
        <KeyCap label="=" side-label="+" />
        <KeyCap delete-key />
      </div>

      <div class="row3">
        <KeyCap tab-key />
        <KeyCap label="Q" />
        <KeyCap label="W" />
        <KeyCap label="E" />
        <KeyCap label="R" />
        <KeyCap label="T" />
        <KeyCap label="Y" />
        <KeyCap label="U" />
        <KeyCap label="I" />
        <KeyCap label="O" />
        <KeyCap label="P" />
        <KeyCap label="[" side-label="{" />
        <KeyCap label="]" side-label="}" />
        <KeyCap label="\" side-label="|" />
      </div>

      <div class="row4">
        <KeyCap cap-key />
        <KeyCap label="A" />
        <KeyCap label="S" />
        <KeyCap label="D" />
        <KeyCap label="F" />
        <KeyCap label="G" />
        <KeyCap label="H" />
        <KeyCap label="J" />
        <KeyCap label="K" />
        <KeyCap label="L" />
        <KeyCap label=";" side-label=":" />
        <KeyCap label="'" side-label='"' />
        <KeyCap return-key />
      </div>

      <div class="row5">
        <KeyCap shift-key-left />
        <KeyCap label="Z" />
        <KeyCap label="X" />
        <KeyCap label="C" />
        <KeyCap label="V" />
        <KeyCap label="B" />
        <KeyCap label="N" />
        <KeyCap label="M" />
        <KeyCap label="," side-label="&lt;" />
        <KeyCap label="." side-label=">" />
        <KeyCap label="/" side-label="?" />
        <KeyCap shift-key-right />
      </div>

      <div class="row6">
        <KeyCap fn-key />
        <KeyCap label="control" side-label="^" ctrl-key />
        <KeyCap label="option" side-label="⌥" ctrl-key />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap spacebar />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap label="option" side-label="⌥" ctrl-key />
        <KeyCap label="&lt;" />
        <div class="square-key-cont">
          <span class="square-content">
            ^
          </span>
          <span class="square-content down-arrow">
            ^
          </span>
        </div>
        <KeyCap label=">" />
      </div>
    </div>
    <div class="trackpad"></div>
  </div>
</template>

<script>
import KeyCap from '@/components/KeyCap.vue';
export default {
  components: {
    KeyCap,
  },
  methods: {
    onKeyDown(evnt) {
      console.log(evnt);
    },
  },
};
</script>

<style lang="scss" scoped>
$rose-gold: #fddbc9;
$key-color: #202124;
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 1%;
  width: 854px;
  height: 598px;
  border: 2px solid $rose-gold;
  border-radius: 35px;
  background: $rose-gold;
}

.key-container {
  display: grid;
  grid-template-rows: repeat(7, auto);
  border: 1px solid #a87961;
  box-shadow: inset 0px 2px 2px 0px #a87961, inset 2px 0px 2px 0px #a87961,
    inset -2px 2px 2px 0px #a87961, inset 0px -2px 2px 0px #a87961;
  width: 780px;
  height: 330px;
  margin: 3.5% 0 0 0;
  border-radius: 12px;
}

.row1 {
  display: flex;
  justify-content: space-around;
  margin: 1% 0.5% 0 0.5%;
}

.row2,
.row3,
.row4,
.row5 {
  display: flex;
  justify-content: space-around;
  margin: 0 0.5% 0 0.5%;
}

.row6 {
  display: flex;
  justify-content: space-around;
  margin: 0 0.5% 0% 0.5%;
}

.f-keys {
  font-size: 0.1em;
  letter-spacing: -0.05em;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  background: $key-color;
  border-radius: 5px;
  border: 2px solid black;
  padding: 0;
  height: 23px;
  width: 48px;
}

.touchID {
  width: 23px;
  border-radius: 5px;
}

.esc {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  font-size: 0.7em;
}

.esc > span:first-of-type {
  margin: 0 0 0 4%;
}

.square-key-cont {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid black;
  background: $key-color;
  height: 45px;
  width: 45px;
  border-radius: 5px;
  font-size: 0.9em;
}

.square-content {
  height: 100%;
}

.delete > span {
  margin: 0 4% 4% 0;
}

.row3 > div,
.row4 > div,
.row5 > div,
.row6 > div {
  justify-content: center;
}

.tab:first-of-type {
  align-items: flex-start;
  justify-content: flex-end;
  width: 70px;
}

.tab > span {
  margin: 0 0 4% 4%;
  font-size: 0.7em;
}

.row4 > .caps {
  align-items: flex-start;
  width: 82px;
}

.return {
  font-size: 0.7em;
  justify-content: flex-end !important;
  align-items: flex-end;
  width: 82px;
}

.return > span:first-of-type {
  margin: 0 4% 4% 0;
}

.lock {
  margin: 0 0 4% 4%;
  font-size: 0.7em;
}

.period {
  margin: 0 0 11% 4%;
}

.shift:first-of-type {
  width: 110px;
  font-size: 0.7em;
  display: flex;
  align-items: flex-start;
  justify-content: flex-end;
}

.shift:first-of-type > span {
  margin: 0 0 4% 4%;
}

.shift:last-of-type {
  width: 110px;
  font-size: 0.7em;
  display: flex;
  align-items: flex-end;
  justify-content: flex-end;
}

.shift:last-of-type > span {
  margin: 0 4% 4% 0;
}

.ctrl {
  margin-top: 20%;
  font-size: 0.7em;
}

.cmd {
  width: 55px;
}

.spacebar {
  width: 260px;
}

.down-arrow {
  transform: rotate(180deg);
}

.trackpad {
  margin: 1% 0;
  width: 320px;
  height: 220px;
  border: 1px solid #9f6e57;
  border-radius: 10px;
}
</style>
