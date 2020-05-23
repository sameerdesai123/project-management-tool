<template>
    <v-container :fluid="true">
      <v-row>
        <v-col v-for="project in projects" :key="project.pid">
          <ProjectMini lg3 md4 sm6 xs8 :project="project"/>
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
