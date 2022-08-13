<template>
  <Box>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || 'Tarefa sem Nome' }}
      </div>
      <div class="column">
        <CountDown :inSeconds="task.duration"/>
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
import ITask from '@/Interface/ITask';
import { defineComponent, PropType} from 'vue'
import CountDown from './CountDown.vue';
import Box from './Box.vue';

export default defineComponent({
    name: "TaksVue",
    props: {
      task:{
        type: Object as PropType<ITask>,
        required: true
      }
    },
    components: { CountDown, Box }
})
</script>
