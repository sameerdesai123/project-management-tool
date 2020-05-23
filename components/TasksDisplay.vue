<template>
  <div>
    <v-expansion-panels
      :inset="true"
    >
      <v-expansion-panel
        v-for="(task,i) in allTasks"
        :key="i"
      >
        <v-expansion-panel-header :class="task.status === strCmpltd ? success : task.status === strPrg ? info : danger">{{ task.taskTitle }}</v-expansion-panel-header>
        <v-expansion-panel-content>
          Status : {{ task.status }} <br/>
          Description : {{ task.taskDescription }} <br/>
          Issues:
          <ol v-for="(issue, j) in task.issues" :key="j">
              <li>{{ issue.name }} : {{ issue.description }}</li>
          </ol>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </div>
</template>

<script>
  export default {
    name: 'TasksDisplay',
    props: {
      allTasks: {
        type: Array,
        default: []
      },
    },
    data() {
      return {
        strCmpltd: 'Completed',
        strPrg: 'In Progress',
        strtodo: 'Pending',
        success: 'success',
        info: 'info',
        danger: 'warning'
      }
    },
    computed: {
      todo () {
        let d = [];
        this.allTasks.forEach(element => {
          if(element.status === 'Pending') d.push(element)
        });
        return d
      },
      doing () {
        let d = [];
        this.allTasks.forEach(element => {
          if(element.status === 'In Progress') d.push(element)
        });
        return d
      },
      coompleted () {
        let d = [];
        this.allTasks.forEach(element => {
          if(element.status === 'Completed') d.push(element)
        });
        return d
      },
    },
  }
</script>

<style lang="sass" scoped>

</style>