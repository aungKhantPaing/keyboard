<template>
  <div class="container" tabindex="-1">
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
        <KeyCap label="`" side-label="~" :isDown="isDown(192)" />
        <KeyCap label="1" side-label="!" :isDown="isDown(49)" />
        <KeyCap label="2" side-label="@" :isDown="isDown(50)" />
        <KeyCap label="3" side-label="#" :isDown="isDown(51)" />
        <KeyCap label="4" side-label="$" :isDown="isDown(52)" />
        <KeyCap label="5" side-label="%" :isDown="isDown(53)" />
        <KeyCap label="6" side-label="^" :isDown="isDown(54)" />
        <KeyCap label="7" side-label="&amp;" :isDown="isDown(55)" />
        <KeyCap label="8" side-label="*" :isDown="isDown(56)" />
        <KeyCap label="9" side-label="(" :isDown="isDown(57)" />
        <KeyCap label="0" side-label=")" :isDown="isDown(48)" />
        <KeyCap label="-" side-label="_" :isDown="isDown(189)" />
        <KeyCap label="=" side-label="+" :isDown="isDown(187)" />
        <KeyCap delete-key :isDown="isDown(8)" />
      </div>

      <div class="row3">
        <KeyCap tab-key :isDown="isDown(9)" />
        <KeyCap label="Q" :isDown="isDown(81)" />
        <KeyCap label="W" :isDown="isDown(87)" />
        <KeyCap label="E" :isDown="isDown(69)" />
        <KeyCap label="R" :isDown="isDown(82)" />
        <KeyCap label="T" :isDown="isDown(84)" />
        <KeyCap label="Y" :isDown="isDown(89)" />
        <KeyCap label="U" :isDown="isDown(85)" />
        <KeyCap label="I" :isDown="isDown(73)" />
        <KeyCap label="O" :isDown="isDown(79)" />
        <KeyCap label="P" :isDown="isDown(80)" />
        <KeyCap label="[" side-label="{" :isDown="isDown(219)" />
        <KeyCap label="]" side-label="}" :isDown="isDown(221)" />
        <KeyCap label="\" side-label="|" :isDown="isDown(220)" />
      </div>

      <div class="row4">
        <KeyCap cap-key :isDown="isDown(20)" />
        <KeyCap label="A" :isDown="isDown(65)" />
        <KeyCap label="S" :isDown="isDown(83)" />
        <KeyCap label="D" :isDown="isDown(68)" />
        <KeyCap label="F" :isDown="isDown(70)" />
        <KeyCap label="G" :isDown="isDown(71)" />
        <KeyCap label="H" :isDown="isDown(72)" />
        <KeyCap label="J" :isDown="isDown(74)" />
        <KeyCap label="K" :isDown="isDown(75)" />
        <KeyCap label="L" :isDown="isDown(76)" />
        <KeyCap label=";" side-label=":" :isDown="isDown(186)" />
        <KeyCap label="'" side-label='"' :isDown="isDown(222)" />
        <KeyCap return-key :isDown="isDown(13)" />
      </div>

      <div class="row5">
        <KeyCap shift-key-left :isDown="isDown(16.1)" />
        <KeyCap label="Z" :isDown="isDown(90)" />
        <KeyCap label="X" :isDown="isDown(88)" />
        <KeyCap label="C" :isDown="isDown(67)" />
        <KeyCap label="V" :isDown="isDown(86)" />
        <KeyCap label="B" :isDown="isDown(66)" />
        <KeyCap label="N" :isDown="isDown(78)" />
        <KeyCap label="M" :isDown="isDown(77)" />
        <KeyCap label="," side-label="&lt;" :isDown="isDown(188)" />
        <KeyCap label="." side-label=">" :isDown="isDown(190)" />
        <KeyCap label="/" side-label="?" :isDown="isDown(191)" />
        <KeyCap shift-key-right :isDown="isDown(16.2)" />
      </div>

      <div class="row6">
        <KeyCap fn-key />
        <KeyCap label="control" side-label="^" ctrl-key :isDown="isDown(17.1)" />
        <KeyCap label="option" side-label="⌥" ctrl-key :isDown="isDown(18.1)" />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap spacebar :isDown="isDown(32)" />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap label="option" side-label="⌥" ctrl-key :isDown="isDown(18.2)" />
        <KeyCap label="&lt;" :isDown="isDown(37)" />
        <div class="square-key-cont">
          <span class="square-content">
            ^
          </span>
          <span class="square-content down-arrow">
            ^
          </span>
        </div>
        <KeyCap label=">" :isDown="isDown(39)" />
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
  data() {
    return {
      downKeys: [],
    };
  },
  methods: {
    isDown(keycode) {
      return this.downKeys.includes(keycode);
    },
  },
  mounted() {
    //! audio note working
    // let keydownSound = new Howl({
    //   src: ['./assets/keydown.mp3'],
    //   volume: 1.0,
    //   autoplay: false,
    // });
    // let keyupSound = new Howl({ src: ['./assets/keyup.mp3'], volume: 1.0, autoplay: false });

    window.addEventListener('keydown', (event) => {
      let keyId = event.keyCode + event.location / 10;
      if (!this.isDown(keyId)) {
        this.downKeys.push(keyId);
      }
      if (keyId == 9) event.preventDefault();
    });
    window.addEventListener('keyup', (event) => {
      let keyId = event.keyCode + event.location / 10;
      this.downKeys = this.downKeys.filter((k) => k != keyId);
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
