<template>
  <div class="scene">
    <div class="case"></div>
    <div class="label"></div>
    <div class="label-text">
      <div class="sticker">
        <div class="tape-description">
          <div class="tape-side">{{tapeSide}}</div>
          <div class="tape-feature">{{tapeFeature}}</div>
        </div>
        <span><slot></slot></span>
      </div>
    </div>
    <div class="band"></div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    tapeSide: {
      type: String,
      default: 'A'
    },
    tapeFeature: {
      type: String,
      default: 'stereo'
    }
  }
})
</script>

<style>
.scene {
  width: 300px;
  height: 200px;
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
  background-image: url('https://source.unsplash.com/random');
  z-index: 0;
  width: 95%;
  height: 70%;
  position: absolute;
  top: 0;
  margin: 3%;
  background-repeat: no-repeat;
  background-size: cover;
  filter: sepia(0.2) saturate(0.8) brightness(0.9);
}

.band {
  background-image: url('~@/assets/cassette_overlay.png');
  z-index: 1;
  width: 100%;
  height: 100%;
  position: absolute;
  background-repeat: no-repeat;
  background-size: contain;

  filter: brightness(0.2);
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
  margin-top: -.1em;
  margin-bottom: -.2em;
  font-size: 1.5em;
}

.tape-feature {
  font-size: .3em;
  text-transform: uppercase;
}

.tape-description ~ span {
  margin-left: .6em;
}
</style>