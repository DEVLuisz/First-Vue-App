<template>
  <main class="columns is-gapless is-multiline" :class="{'dark-mode' : modoEscuro}">
    <div class="column is-one-quarter">
        <BarraLateral @aoTemaAlterado="changeTheme"/>
    </div>

    <div class="column is-three-quarter context">
        <Forms @saveTask="saveTask"/>
        <div class="lista">
          <Task v-for="(task, index) in tasks" :key="index" :task="task"/>
        <Box v-if="listEmpty">
          Você não está muito produtivo hoje! :(
        </Box>
        </div> 
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Forms from './components/Forms.vue';
import Task from './components/Task.vue';
import ITask from './Interface/ITask'
import Box from './components/Box.vue';
export default defineComponent({
    name: "App",
    data() {
      return{
        tasks: [] as ITask[],
        modoEscuro: false
      }
    },
    computed: {
      listEmpty() : boolean {
        return this.tasks.length === 0
      }
    },
    methods: {
      saveTask(task: ITask){
        this.tasks.push(task)
      },
      changeTheme(modoEscuro: boolean){
        this.modoEscuro = modoEscuro
      }
    },
    components: { BarraLateral, Forms, Task, Box }
});
</script>

<style>
  .lista{
    padding: 1.15rem;
  }

  main {
    --bg-primario: #FFF;
    --text-primario: #000;
  }

  main.dark-mode {
    --bg-primario: rgb(25, 77, 51);
    --text-primario: #CCC;
  }

  .context {
    background-color: var(--bg-primario);
  }
</style>
