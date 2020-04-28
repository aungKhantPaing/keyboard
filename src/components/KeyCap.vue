<template>
  <div
    v-if="!spacebar"
    class="square-key-cont"
    :class="{
      delete: deleteKey,
      tab: tabKey,
      caps: capKey,
      return: returnKey,
      'shift-left': shiftKeyLeft,
      'shift-right': shiftKeyRight,
      fn: fnKey,
      cmd: cmdKey,
      'keydown-style': isDown,
    }"
  >
    <span v-if="sideLabel" class="square-content">
      {{ sideLabel }}
    </span>
    <span :class="{ 'square-content': sideLabel || capKey, period: capKey, ctrl: ctrlKey }">
      {{ label }}
    </span>

    <span v-if="deleteKey">
      delete
    </span>
    <span v-else-if="tabKey">
      tab
    </span>
    <span v-else-if="capKey" class="square-content lock">
      caps lock
    </span>
    <span v-else-if="returnKey" class="return-span">return</span>
    <span v-else-if="shiftKeyLeft || shiftKeyRight">
      shift
    </span>
    <span v-else-if="fnKey">
      fn
    </span>
  </div>
  <div v-else class="square-key-cont spacebar" :class="{ 'keydown-style': isDown }"></div>
</template>

<script>
import { Howl, Howler } from 'howler';
export default {
  props: {
    label: {
      type: String,
    },
    sideLabel: {
      type: String,
      default: '',
    },
    deleteKey: {
      type: Boolean,
      default: false,
    },
    tabKey: {
      type: Boolean,
      default: false,
    },
    capKey: {
      type: Boolean,
      default: false,
    },
    returnKey: {
      type: Boolean,
      default: false,
    },
    shiftKeyLeft: {
      type: Boolean,
      default: false,
    },
    shiftKeyRight: {
      type: Boolean,
      default: false,
    },
    fnKey: {
      type: Boolean,
      default: false,
    },
    ctrlKey: {
      type: Boolean,
      default: false,
    },
    cmdKey: {
      type: Boolean,
      default: false,
    },
    spacebar: {
      type: Boolean,
      default: false,
    },
    keyCode: {
      type: Number,
      default: null,
    },
  },
  data() {
    return {
      isDown: false,
    };
  },
  mounted() {
    //! audio note working
    // let keydownSound = new Howl({
    //   src: ['./assets/keydown.mp3'],
    //   volume: 1.0,
    //   autoplay: false,
    // });
    // let keyupSound = new Howl({ src: ['./assets/keyup.mp3'], volume: 1.0, autoplay: false });
    if (this.keyCode) {
      window.addEventListener('keydown', (event) => {
        if (event.keyCode == this.keyCode) {
          if (!this.isDown) {
            console.warn('*DOWN: ' + event.keyCode);
          }
          this.isDown = true;
        }
      });
      window.addEventListener('keyup', (event) => {
        if (event.keyCode == this.keyCode) {
          if (this.isDown) {
            console.warn('*UP: ' + event.keyCode);
          }
          this.isDown = false;
        }
      });
    }
  },
};
</script>

<style lang="scss" scoped>
$rose-gold: #fddbc9;
$key-color: #202124;

.keydown-style {
  border: 2px solid $rose-gold !important;
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
  color: white;
}
.square-content {
  height: 100%;
}

//* DELETE
.delete {
  font-size: 0.7em !important;
  justify-content: flex-end !important;
  align-items: flex-end !important;
  width: 70px !important;
}
.delete > span:last-of-type {
  margin: 0 4% 4% 0;
}

//* TAB
.tab {
  align-items: flex-start;
  justify-content: flex-end;
  width: 70px;
}
.tab > span:last-of-type {
  margin: 0 0 4% 4%;
  font-size: 0.7em;
}

//* CAPS
.caps {
  align-items: flex-start;
  width: 82px;
}
.lock {
  margin: 0 0 4% 4%;
  font-size: 0.7em;
}
.period {
  margin: 0 0 11% 4%;
}

//* RETURN
.return {
  font-size: 0.7em;
  justify-content: flex-end !important;
  align-items: flex-end;
  width: 82px;
}
.return > span:last-of-type {
  margin: 0 4% 4% 0;
}

//* SHIFT
.shift-left {
  width: 110px !important;
  font-size: 0.7em !important;
  display: flex !important;
  align-items: flex-start !important;
  justify-content: flex-end !important;
}
.shift-left > span:last-of-type {
  margin: 0 0 4% 4%;
}
.shift-right {
  width: 110px !important;
  font-size: 0.7em !important;
  display: flex !important;
  align-items: flex-end !important;
  justify-content: flex-end !important;
}
.shift-right > span {
  margin: 0 4% 4% 0;
}

//* Fn
.fn {
  font-size: 0.7em !important;
  display: flex !important;
  align-items: flex-start !important;
  justify-content: flex-end !important;
  width: 45px !important;
}
.fn > span {
  margin: 0 0 4% 6%;
}

//* CTRL
.ctrl {
  margin-top: 20%;
  font-size: 0.7em;
}

//* CMD
.cmd {
  width: 55px !important;
}

//*SPACE
.spacebar {
  width: 260px !important;
}
</style>
