<template>
  <div class="hello">
    <form class="task-form">
      <h2>Tarea</h2>
      <input v-model="task" placeholder="Ingresa nueva tarea"/>
      <button @click="onAdd($event)">Añade</button>
    </form>
    <ul>
      <li v-for="(el,idx)  in tasks" :key="idx"><Hijo @onDeleteTask='onDeleteTask' :id=idx :task=el /></li>
    </ul>
  </div>
</template>

<script>
import Hijo from './Hijo.vue';

export default {
  name: 'Padre',
  data() {
    return {
      tasks: [],
      task: ''
    }
  },
  components: {
    Hijo,
  },
  methods: {
    onAdd(event) {
      event.preventDefault();
      if(!(this.task.trim() === '')){
        this.tasks.push(this.task);
        this.task = '';
      }
    },
    onDeleteTask(id){
      console.log(id)
      this.tasks.splice(id,1);
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 5px 10px;
}
a {
  color: #42b983;
}

.task-form{
  display: flex;
  justify-content: center;
  align-items: center;
  * {
    margin: 0 5px;
  }
}
</style>
