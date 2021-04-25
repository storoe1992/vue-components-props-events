<template>
  <div>
      <div class="task">
        <h2>{{task}}</h2>
        <button @click="onDelete">eliminar</button>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Hijo',
    props: {
        id: {
            type: Number,
            require: true
        },
        task: {
            type: String,
            require: true
        }
    },
    methods: {
        onDelete() {
            this.$emit('onDeleteTask',this.id);
        }
    },
}
</script>

<style scoped lang="scss">
    .task{
        display: flex;
        justify-content: center;
        align-items: left;

        * {
           margin: 0 5px;
        }
    }
</style>