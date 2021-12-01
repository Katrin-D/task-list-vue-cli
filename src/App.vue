<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <input type="text" 
          v-bind:placeholder='placeholderStr' 
          v-bind:value='inputValue' 
          v-on:input='inputHandler' 
          v-on:keypress.enter='addTask'

          />
    <AddButton v-on:click='addTask'/>
    <button class="deleleAll_btn" v-on:click="deleleAll">Очистить список</button>
    <List v-bind:tasks='tasks'
          v-on:delete-task='deleteTask'
          />
 </div>
</template>

<script>
import List from './components/List.vue'
import AddButton from './components/AddButton.vue'


export default {
  name: 'App',
  data() {
    return {
      title: 'Список задач',
      placeholderStr: 'Введите задачу',
      inputValue: '',
      tasks: [
      {text:'Выслать отчёт', completed: false}, 
      {text:'Забронировать билеты в кино', completed: false}, 
      {text:'Купить коту корм', completed: false},
      ],
            }
          },
  components: {
    List,
    AddButton,
    
  },
  methods: {
    inputHandler(event) {
      this.inputValue = event.target.value;
      console.log(event.target.value); 
    },

    addTask() {
      
      if (this.inputValue !== '') {
        const newTask = {text:this.inputValue, completed: false};
        this.tasks.push(newTask);
        this.inputValue = '';
        console.log("test");
      }
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    deleleAll() {
      this.tasks.splice(this.tasks);
    }

  }
}
</script>

<style>
</style>
