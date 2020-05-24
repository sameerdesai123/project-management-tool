<template>
  <div>
    <v-expansion-panels
      :inset="true"
    >
      <v-expansion-panel
        v-for="(task,i) in allTasks"
        :key="i"
      >
        <v-expansion-panel-header>{{ task.taskTitle }} &nbsp;
          <span>
            <v-chip :class="task.status === strCmpltd ? success : task.status === strPrg ? info : danger">
              {{ task.status }}
            </v-chip>
            <v-btn :class="task.status === strCmpltd ? success : task.status === strPrg ? info : danger" x-small>
            {{ btnFunc(task.status) }}
            <span v-if="btnFunc(task.status) === 'Reopen'"><v-icon>mdi-plus</v-icon></span>
            <span v-if="btnFunc(task.status) === 'Mark as Done'"><v-icon>mdi-checkbox-marked-circle-outline</v-icon></span>
            <span v-if="btnFunc(task.status) === 'Begin'"><v-icon>mdi-near-me</v-icon></span>
          </v-btn>
          </span>
        </v-expansion-panel-header>
        <v-expansion-panel-content>
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
    methods: {
      btnFunc (status) {
        if( status === 'Completed') return 'Reopen'
        else if( status === 'In Progress') return 'Mark as Done'
        else return 'Begin'
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
.btnFunc
  width: 50px  
</style>