<template>
  <v-card
  class="mx-auto"
  max-width="500"
  :hover="true"
  >
  <nuxt-link 
  class="project-link" 
  :to="{name: 'projects-id', params: { id: project.pid } }">
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
  </nuxt-link>
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
.project-link {
  text-decoration: none;
  color: whitesmoke;
}

</style>