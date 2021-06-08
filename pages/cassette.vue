<template>
  <div>
    <Casette tape-feature="stereo" tape-side="B" :completion="completion"
      >Tape No. 1</Casette
    >
    <input
      v-model.number="completion"
      type="range"
      min="0"
      max="100"
      value="0"
    />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Casette from '~/components/Cassette.vue'
export default Vue.extend({
  components: { Casette },
  data() {
    return {
      completion: 0 as number,
      forward: true as boolean,
    }
  },
  mounted() {
    setInterval(() => {
      this.completion = this.completion + (this.forward ? 0.1 : -0.1)
      if (this.completion > 100 || this.completion < 0)
        this.forward = !this.forward
    }, 60)
  },
})
</script>
