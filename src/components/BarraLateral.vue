<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Logo Vue" />
    </h1>
    <button class="button" @click="alterarTema">
      {{ textButton }}
    </button>
  </header>
</template>

<script lang="ts">
  import { defineComponent} from 'vue';

  export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data() {
      return {
        modoEscuro: false
      }
    },
    computed:{
      textButton() {
        if(this.modoEscuro) {
          return 'Desativar Dark Mode'
        }
          return 'Ativar Dark Mode'
      }
    },
    methods: {
      alterarTema () {
        this.modoEscuro = !this.modoEscuro
        this.$emit('aoTemaAlterado', this.modoEscuro)
      }
    }
  })
</script>

<style>
  header {
  padding: 1rem 3.5rem;
  background: #7FFFD4;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>