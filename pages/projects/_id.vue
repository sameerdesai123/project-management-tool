<template>
  <div>
    Welcome to project {{ id }}
    <h1>{{ project.name }}</h1>
    <TasksDisplay :allTasks="project.tasks"/>
  </div>
</template>

<script>
import TasksDisplay from '@/components/TasksDisplay.vue'

  export default {
    name: 'id-view',
    components: {
      TasksDisplay,
    },
    computed: {
      id () {
        return this.$route.params.id
      },
      project () {
        // Edit this later
        return this.$store.state.projects.projects[parseInt(this.id) - 101]
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>