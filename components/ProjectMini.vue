<template>
  <v-card
  class="mx-auto"
  max-width="500"
  :hover="true"
  >
    <v-card-title>
      {{ project.name }}
    </v-card-title>
    <v-card-subtitle>
      {{ project.description }}
    </v-card-subtitle>
    <v-card-text>
      <v-row>
        <v-col>Total Tasks:  {{ project.totalTasksCount }}</v-col>
        <v-col>To Do: {{ project.todoCount }}</v-col>
      </v-row>
      <v-row>
        <v-col>Completed: {{ project.completedCount }}</v-col>
        <v-col>In Progress: {{ project.inProcess }}</v-col>
      </v-row>
    </v-card-text>
    <v-card-actions>
      <v-btn icon>
        <v-icon>mdi-bookmark</v-icon>
      </v-btn>
      <v-btn icon>
        <a :href="project.github" target="_blank" rel="noopener noreferrer"><v-icon>mdi-github</v-icon></a>
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
  export default {
    name: 'ProjectMini',
    props: {
      project: {
        type: Object,
        default: {}
      },
    },
  }
</script>

<style scoped>

</style>