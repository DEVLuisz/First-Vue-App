<template>
<section>
        <strong class="display">
          {{ timeStarted }}
          </strong>
      </section>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: 'CountDown',
  props:{
    inSeconds: {
      type: Number,
      default: 0
    }
  },
      computed: {
      timeStarted (): string {
        return new Date(this.inSeconds * 1000).toISOString().substr(11, 8);
      }
    }
})

</script>

<style>
  .display{
    color: var(--text-primario);
  }
</style>