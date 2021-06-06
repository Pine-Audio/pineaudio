<template>
  <div>
    <Casette tape-feature="stereo" tape-side="B" :completion="completion"
      >My cool Mixtape!!</Casette
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
    }
  },
  mounted() {
    setInterval(() => {
      this.completion = this.completion + 0.1
    }, 60)
  },
})
</script>
