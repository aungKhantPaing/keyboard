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
        <KeyCap label="`" side-label="~" :key-code="192" />
        <KeyCap label="1" side-label="!" :key-code="49" />
        <KeyCap label="2" side-label="@" :key-code="50" />
        <KeyCap label="3" side-label="#" :key-code="51" />
        <KeyCap label="4" side-label="$" :key-code="52" />
        <KeyCap label="5" side-label="%" :key-code="53" />
        <KeyCap label="6" side-label="^" :key-code="54" />
        <KeyCap label="7" side-label="&amp;" :key-code="55" />
        <KeyCap label="8" side-label="*" :key-code="56" />
        <KeyCap label="9" side-label="(" :key-code="57" />
        <KeyCap label="0" side-label=")" :key-code="48" />
        <KeyCap label="-" side-label="_" :key-code="189" />
        <KeyCap label="=" side-label="+" :key-code="187" />
        <KeyCap delete-key />
      </div>

      <div class="row3">
        <KeyCap tab-key />
        <KeyCap label="Q" :key-code="81" />
        <KeyCap label="W" :key-code="87" />
        <KeyCap label="E" :key-code="69" />
        <KeyCap label="R" :key-code="82" />
        <KeyCap label="T" :key-code="84" />
        <KeyCap label="Y" :key-code="89" />
        <KeyCap label="U" :key-code="85" />
        <KeyCap label="I" :key-code="73" />
        <KeyCap label="O" :key-code="79" />
        <KeyCap label="P" :key-code="80" />
        <KeyCap label="[" side-label="{" />
        <KeyCap label="]" side-label="}" />
        <KeyCap label="\" side-label="|" />
      </div>

      <div class="row4">
        <KeyCap cap-key />
        <KeyCap label="A" :key-code="65" />
        <KeyCap label="S" :key-code="83" />
        <KeyCap label="D" :key-code="68" />
        <KeyCap label="F" :key-code="70" />
        <KeyCap label="G" :key-code="71" />
        <KeyCap label="H" :key-code="72" />
        <KeyCap label="J" :key-code="74" />
        <KeyCap label="K" :key-code="75" />
        <KeyCap label="L" :key-code="76" />
        <KeyCap label=";" side-label=":" />
        <KeyCap label="'" side-label='"' />
        <KeyCap return-key />
      </div>

      <div class="row5">
        <KeyCap shift-key-left />
        <KeyCap label="Z" :key-code="90" />
        <KeyCap label="X" :key-code="88" />
        <KeyCap label="C" :key-code="67" />
        <KeyCap label="V" :key-code="86" />
        <KeyCap label="B" :key-code="66" />
        <KeyCap label="N" :key-code="78" />
        <KeyCap label="M" :key-code="77" />
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
        <KeyCap spacebar :key-code="32" />
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
  mounted() {
    window.addEventListener('keypress', (event) => {
      console.log('PRESSED: ' + event.key + ' | ' + event.keyCode);
    });
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
  padding: 0px;
  box-sizing: unset;
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
  font-size: 0.1em !important;
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
  font-size: 0.7em !important;
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

.fn > span {
  margin: 0 0 4% 6%;
}
</style>
