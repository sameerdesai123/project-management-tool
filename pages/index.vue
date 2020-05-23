<template>
    <v-container :fluid="true">
      <v-row>
        <v-col v-for="project in projects" :key="project.pid">
          <ProjectMini class="min-w-270" :project="project"/>
        </v-col>
      </v-row>
    </v-container>
</template>

<script>
import ProjectMini from '@/components/ProjectMini.vue'

export default {
  components: {
    ProjectMini,
  },
  data() {
    return {
      projects: []
    }
  },
  mounted () {
    this.projects = this.$store.state.projects.projects;
    console.log(this.projects);
    
  },
}
</script>

<style scoped>
.min-w-270 {
  min-width: 250px;
}
</style>
