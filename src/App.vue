<template>
  <div class="container">
    <h3 class="text-center">Vue To do Application</h3>
    
    <div class="d-flex">
      <input type="text" @keydown.enter="Add" v-model="task" class="form-control" placeholder="Enter your task">
    <button class="btn btn-primary" @click="Add">ADD</button>
    </div>
    <div class="table-responsive">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">Task</th>
            <th scope="col">#</th>
            <th scope="col">#</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item,index) in tasks" :key="index">
            <th scope="row">{{index+1}}</th>
            <td :class="{'finished' : item.finished == true}">{{item.task}}</td>
            <td><i class="fas fa-check addPointer" @click="Finished(index)"></i></td>
            <td><i class="far fa-trash-alt addPointer" @click="Delete(index)"></i></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      task: null,
      tasks:[],
    }
  },
  methods:{
    Add(){
      if(this.task != null){
        this.tasks.push({
          task: this.task,
          finished: false
          });
        this.task = null;
      }
    },
    Delete(index){
      this.tasks.splice(index,1);
    },
    Finished(index){
      this.tasks[index].finished = !this.tasks[index].finished;
    }
  }
};
</script>

<style>
.addPointer{
  cursor: pointer;
}
.finished{
  text-decoration: line-through;
}
</style>