<template>
<div class="box formulario">
  <div class="columns">
    <div class="column is-8" role="form" aria-label="create a new todo">
      <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?"
      v-model="descricao"/>
    </div>
    <div class="column">
      <Temporize @inTimeEnd="finishTodo"/>
    </div>
  </div>
</div>
</template>

<script lang="ts">
  import { defineComponent} from 'vue';
  import Temporize from './Temporize.vue';

  export default defineComponent({
    name: "FormsCreated",
    emits: ['saveTask'],
    data(){
      return {
        descricao: ''
      }
    },
    methods: {
      finishTodo(timeStarted: number) : void{
        this.$emit('saveTask', {
          duration: timeStarted,
          description: this.descricao
        })
        this.descricao = ''
      }
    },
    components: { Temporize }
})
</script>

<style>
  .formulario{
    color: var(--text-primario);
    background-color: var(--bg-primario);
  }
</style>