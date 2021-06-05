<template>
  <Casette tape-feature="MONO" tape-side="B">My cool Mixtape!!</Casette>
</template>

<script lang="ts">
import Vue from 'vue'
import Casette from '~/components/Cassette.vue'
export default Vue.extend({
  components: { Casette },
})
</script>
