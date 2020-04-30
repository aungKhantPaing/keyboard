<template>
  <div class="container" tabindex="-1">
    <div class="key-container">
      <div class="row1">
        <KeyCap f-key esc-key :isDown="keysState.get(27)" />
        <KeyCap label="F1" f-key />
        <KeyCap label="F2" f-key />
        <KeyCap label="F3" f-key />
        <KeyCap label="F4" f-key />
        <KeyCap label="F5" f-key />
        <KeyCap label="F6" f-key />
        <KeyCap label="F7" f-key />
        <KeyCap label="F8" f-key />
        <KeyCap label="F9" f-key />
        <KeyCap label="F10" f-key />
        <KeyCap label="F11" f-key />
        <KeyCap label="F12" f-key />
        <span class="touchID f-keys"></span>
      </div>

      <div class="row2">
        <KeyCap label="`" side-label="~" :isDown="keysState.get(192)" />
        <KeyCap label="1" side-label="!" :isDown="keysState.get(49)" />
        <KeyCap label="2" side-label="@" :isDown="keysState.get(50)" />
        <KeyCap label="3" side-label="#" :isDown="keysState.get(51)" />
        <KeyCap label="4" side-label="$" :isDown="keysState.get(52)" />
        <KeyCap label="5" side-label="%" :isDown="keysState.get(53)" />
        <KeyCap label="6" side-label="^" :isDown="keysState.get(54)" />
        <KeyCap label="7" side-label="&amp;" :isDown="keysState.get(55)" />
        <KeyCap label="8" side-label="*" :isDown="keysState.get(56)" />
        <KeyCap label="9" side-label="(" :isDown="keysState.get(57)" />
        <KeyCap label="0" side-label=")" :isDown="keysState.get(48)" />
        <KeyCap label="-" side-label="_" :isDown="keysState.get(189)" />
        <KeyCap label="=" side-label="+" :isDown="keysState.get(187)" />
        <KeyCap delete-key :isDown="keysState.get(8)" />
      </div>

      <div class="row3">
        <KeyCap tab-key :isDown="keysState.get(9)" />
        <KeyCap label="Q" :isDown="keysState.get(81)" />
        <KeyCap label="W" :isDown="keysState.get(87)" />
        <KeyCap label="E" :isDown="keysState.get(69)" />
        <KeyCap label="R" :isDown="keysState.get(82)" />
        <KeyCap label="T" :isDown="keysState.get(84)" />
        <KeyCap label="Y" :isDown="keysState.get(89)" />
        <KeyCap label="U" :isDown="keysState.get(85)" />
        <KeyCap label="I" :isDown="keysState.get(73)" />
        <KeyCap label="O" :isDown="keysState.get(79)" />
        <KeyCap label="P" :isDown="keysState.get(80)" />
        <KeyCap label="[" side-label="{" :isDown="keysState.get(219)" />
        <KeyCap label="]" side-label="}" :isDown="keysState.get(221)" />
        <KeyCap label="\" side-label="|" :isDown="keysState.get(220)" />
      </div>

      <div class="row4">
        <KeyCap cap-key :capOn="capOn" :isDown="keysState.get(20)" />
        <KeyCap label="A" :isDown="keysState.get(65)" />
        <KeyCap label="S" :isDown="keysState.get(83)" />
        <KeyCap label="D" :isDown="keysState.get(68)" />
        <KeyCap label="F" :isDown="keysState.get(70)" />
        <KeyCap label="G" :isDown="keysState.get(71)" />
        <KeyCap label="H" :isDown="keysState.get(72)" />
        <KeyCap label="J" :isDown="keysState.get(74)" />
        <KeyCap label="K" :isDown="keysState.get(75)" />
        <KeyCap label="L" :isDown="keysState.get(76)" />
        <KeyCap label=";" side-label=":" :isDown="keysState.get(186)" />
        <KeyCap label="'" side-label='"' :isDown="keysState.get(222)" />
        <KeyCap return-key :isDown="keysState.get(13)" />
      </div>

      <div class="row5">
        <KeyCap shift-key-left :isDown="keysState.get(16.1)" />
        <KeyCap label="Z" :isDown="keysState.get(90)" />
        <KeyCap label="X" :isDown="keysState.get(88)" />
        <KeyCap label="C" :isDown="keysState.get(67)" />
        <KeyCap label="V" :isDown="keysState.get(86)" />
        <KeyCap label="B" :isDown="keysState.get(66)" />
        <KeyCap label="N" :isDown="keysState.get(78)" />
        <KeyCap label="M" :isDown="keysState.get(77)" />
        <KeyCap label="," side-label="&lt;" :isDown="keysState.get(188)" />
        <KeyCap label="." side-label=">" :isDown="keysState.get(190)" />
        <KeyCap label="/" side-label="?" :isDown="keysState.get(191)" />
        <KeyCap shift-key-right :isDown="keysState.get(16.2)" />
      </div>

      <div class="row6">
        <KeyCap fn-key />
        <KeyCap label="control" side-label="^" ctrl-key :isDown="keysState.get(17.1)" />
        <KeyCap label="option" side-label="⌥" ctrl-key :isDown="keysState.get(18.1)" />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap spacebar :isDown="keysState.get(32)" />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap label="option" side-label="⌥" ctrl-key :isDown="keysState.get(18.2)" />
        <KeyCap label="&lt;" :isDown="keysState.get(37)" />
        <div class="arrow-key-cont">
          <KeyCap arrow-key :isDown="keysState.get(38)" />
          <KeyCap arrow-key :isDown="keysState.get(40)" down-arrow />
        </div>
        <KeyCap label=">" :isDown="keysState.get(39)" />
      </div>
    </div>
    <div class="trackpad"></div>
  </div>
</template>

<script>
import KeyCap from '@/components/KeyCap.vue';
import { Howl, Howler } from 'howler';

export default {
  components: {
    KeyCap,
  },
  data() {
    return {
      keysState: new Map(
        Array(223)
          .fill()
          .map((_, i) => i)
          .concat([16.1, 16.2, 17.1, 17.2, 18.1, 18.2])
          .map((k) => [k, false]),
      ),
      capOn: false,
    };
  },
  mounted() {
    const keydownSound = new Howl({
        src: ['/keydown.mp3'],
      }),
      keyupSound = new Howl({
        src: ['/keyup.mp3'],
      });
    Howler.volume(0.3);
    document.addEventListener('keydown', (event) => {
      let keyId = event.keyCode + event.location / 10;
      if (!this.keysState.get(keyId)) {
        keydownSound.play();

        let newMapValue = new Map([[keyId, true]]);
        this.keysState = new Map([...this.keysState, ...newMapValue]);
        // this.downKeys.push(keyId);

        if (keyId == 9) event.preventDefault(); // prevent from tabbing out
        if (keyId == 20)
          this.capOn = !(event.getModifierState && event.getModifierState('CapsLock'));
      }
    });
    document.addEventListener('keyup', (event) => {
      keyupSound.play();
      let keyId = event.keyCode + event.location / 10;

      let newMapValue = new Map([[keyId, false]]);
      this.keysState = new Map([...this.keysState, ...newMapValue]);
      // this.downKeys = this.downKeys.filter((k) => k != keyId);
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
  font-size: 0.5em !important;
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

.arrow-key-cont {
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 5px;
  font-size: 0.9em;
  height: 49px;
  background-color: $rose-gold;
}

.arrow-content {
  flex-direction: column;
  background: $key-color;
  align-items: center;
  border: 2px solid black;
  border-bottom: 1px solid black;
  display: flex;
  border-radius: 5px 5px 0px 0px;
  height: 22.5px;
  width: 45px;
}

.down-arrow {
  transform: rotate(180deg);
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
