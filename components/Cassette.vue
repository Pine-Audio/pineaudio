<template>
  <div class="scene">
    <div class="case"></div>
    <div class="label"><img src="https://source.unsplash.com/random" /></div>
    <div class="label-text">
      <div class="sticker">
        <div class="tape-description">
          <div class="tape-side">{{ tapeSide }}</div>
          <div class="tape-feature">{{ tapeFeature }}</div>
        </div>
        <span><slot></slot></span>
      </div>
    </div>
    <div class="band">
      <div class="cover"></div>
      <div id="left" class="bit" :style="rotationCSS"></div>
      <div id="right" class="bit" :style="[rotationCSS]"></div>
    </div>
    <div id="left" class="tape" :style="sizeLeft"></div>
    <div id="right" class="tape" :style="sizeRight"></div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    tapeSide: {
      type: String,
      default: 'A',
    },
    tapeFeature: {
      type: String,
      default: 'stereo',
    },
    rotation: {
      type: Number,
      default: 0,
    },
    completion: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    rotationCSS(): object {
      return {
        transform: 'rotate(-' + this.completion * 100 + 'deg)',
      }
    },
    sizeLeft(): object {
      const scale: number = 1 - (0.5 / 100) * this.completion
      return {
        transform: 'scale(' + scale + ')',
      }
    },
    sizeRight(): object {
      const scale: number = (0.5 / 100) * this.completion + 0.5
      return {
        transform: 'scale(' + scale + ')',
      }
    },
  },
})
</script>

<style>
.scene {
  width: 509px;
  height: 320px;
  position: relative;
  zoom: 1;
}

.case {
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url('~@/assets/cassette.png');
  background-repeat: no-repeat;
  z-index: 2;
  background-size: contain;

  filter: brightness(0.2);
}

.label {
  z-index: 1;
  position: absolute;
  top: 0;
  filter: sepia(0.2) saturate(0.8) brightness(0.9);
  overflow: hidden;
  height: 100%;
}

.label img {
  width: 100%;
  object-fit: cover;
  mask-size: 100%;
  mask-image: url('~@/assets/cassette_mask_no_bits.png');
  mask-position: 0px 0px;
}

.band {
  filter: brightness(0.2);
  width: 100%;
  height: 100%;
  z-index: 3;
  position: relative;
}

.cover {
  background-image: url('~@/assets/cassette_overlay_no_bits.png');
  z-index: 5;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  position: absolute;
  background-repeat: no-repeat;
  background-size: contain;
}

.label-text {
  font-family: Helvetica, sans-serif;
  width: 100%;
  height: 15%;
  margin-top: 8%;
  z-index: 5;
  position: absolute;
  display: flex;
}

.sticker {
  background-color: #ebebeb;
  background-image: url('~@/assets/notebook-dark.png');
  background-size: 30%;
  margin-left: 8%;
  margin-right: 9%;
  border-radius: 3px;
  width: 100%;
  display: flex;
  align-items: center;
  padding-left: 0.5em;
  box-shadow: 2px 2.5px 10px -7px #000000;
}

.tape-description {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tape-side {
  margin-top: -0.1em;
  margin-bottom: -0.2em;
  font-size: 1.5em;
}

.tape-feature {
  font-size: 0.3em;
  text-transform: uppercase;
}

.tape-description ~ span {
  margin-left: 0.6em;
}

.bit {
  background-image: url('~@/assets/cassette_bits.svg');
  z-index: 3;
  width: 49px;
  height: 49px;
  position: absolute;
  transition: transform 0.3s;
}

.bit#left {
  top: 37.5%;
  left: 24.2%;
}

.bit#right {
  top: 37.5%;
  left: 66%;
}

.tape {
  background: radial-gradient(
      circle,
      rgba(145, 145, 145, 0.2),
      rgba(46, 46, 46, 0.2)
    ),
    radial-gradient(
      circle,
      transparent 35%,
      rgb(29, 37, 43) 30px,
      rgb(29, 37, 43) 10%,
      rgb(11, 13, 15) 10%,
      rgb(11, 13, 15) 11%,
      rgb(29, 37, 43) 11%,
      rgb(29, 37, 43) 20%,
      rgb(11, 13, 15) 20%,
      rgb(11, 13, 15) 21%,
      rgb(29, 37, 43) 21%,
      rgb(29, 37, 43) 30%,
      rgb(11, 13, 15) 30%,
      rgb(11, 13, 15) 31%,
      rgb(29, 37, 43) 31%,
      rgb(29, 37, 43) 40%,
      rgb(11, 13, 15) 40%,
      rgb(11, 13, 15) 41%,
      rgb(29, 37, 43) 41%,
      rgb(29, 37, 43) 50%,
      rgb(11, 13, 15) 50%,
      rgb(11, 13, 15) 51%,
      rgb(29, 37, 43) 51%,
      rgb(29, 37, 43) 60%,
      rgb(11, 13, 15) 60%,
      rgb(11, 13, 15) 61%,
      rgb(29, 37, 43) 61%,
      rgb(29, 37, 43) 70%,
      rgb(11, 13, 15) 70%,
      rgb(11, 13, 15) 71%,
      rgb(29, 37, 43) 71%,
      rgb(29, 37, 43) 80%,
      rgb(11, 13, 15) 80%,
      rgb(11, 13, 15) 81%,
      rgb(29, 37, 43) 81%,
      rgb(29, 37, 43) 90%,
      rgb(11, 13, 15) 90%,
      rgb(11, 13, 15) 91%,
      rgb(29, 37, 43) 91%,
      rgb(29, 37, 43) 100%
    );
  z-index: 0;
  border-radius: 50%;
  position: absolute;
  transition: transform 0.2;
  transform-origin: center;
}

.tape#left {
  left: 9.5%;
  top: 14%;
  width: 200px;
  height: 200px;
}

.tape#right {
  left: 50.8%;
  top: 14%;
  width: 200px;
  height: 200px;
}
</style>
