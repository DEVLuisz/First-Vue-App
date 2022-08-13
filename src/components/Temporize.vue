<template>
      <div class="is-flex is-align-items-center is-justify-content-space-between">
      <CountDown :inSeconds="inSeconds"/>
      <button class="button" @click="started" :disabled="cronometroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>Play</span>
        </button>
        <button class="button" @click="finish" :disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>Stop</span>
        </button>
      </div>
</template>


<script lang="ts">
  import { defineComponent} from 'vue';
import CountDown from './CountDown.vue';

  export default defineComponent({
    name: "TimeIn",
    emits: ['inTimeEnd'],
    data() {
        return {
            inSeconds: 0,
            cronometro: 0,
            cronometroRodando: false
        };
    },
    methods: {
        started() {
          this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.inSeconds += 1;
            }, 1000);
        },
        finish() {
          this.cronometroRodando = false
            clearInterval(this.cronometro);
            this.$emit('inTimeEnd', this.inSeconds)
            this.inSeconds = 0
        }
    },
    components: { CountDown }
})
</script>