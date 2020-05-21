<template>
  <div class="home">
    <div class="wrap"><input type="text" v-model="state.current"></div>
    <todo-item
      v-for="item in state.todos"
      :key="item.name"
      :name="item.name"
      :marked="item.marked"
      :done="item.done"
      :class="item.done ?'done' : ''"
      @close="item.marked = !item.marked"
      @done="item.done = !item.done"
      />
    <button @click="addOne()" class="add">Добавить</button>
  </div>
</template>

<script>
// @ is an alias to /src
import toDoItem from '@/components/toDoItem'

export default {
  name: 'Home',
  data(){
    return{
      state: {
        todos: [
          {id:1, name: 'Погладить', marked: false, done:true},
          {id:2, name: 'Постирать', marked: true, done:false},
          {id:3, name: 'Кино', marked: false, done:false},
          {id:4, name: 'Звонок', marked: true, done:false},
          {id:5, name: 'Диплом', marked: false, done:false},
        ],
        current: ''
      }
    }
  },
  components:{
    'todo-item' : toDoItem
  },
  methods: {
    addOne: function(){
      const letter = this.state.current
      this.state.todos.push({id:25, name: letter, marked:false, done: false})
      this.state.current = ''
    },
    // close: function(e){
    //   console.log(e)
    // }
  }
}
</script>

<style lang="scss" scoped>
.home{
  width: 900px;
  margin: 0 auto;
  font-size: 26px;
  padding: 20px 10px;
  border: 1px solid #000;
  .wrap{
    input{
      width: 100%;
      height: 50px;
    }
  }
  .item{
    text-align: left;
    margin-bottom: 10px;
    padding: 10px;
  }
  .add{
    height: 50px;
    border: 1px solid #000;
    border-radius: 25px;
    font-size: 26px;
  }
  .done{
    text-decoration: line-through;
  }
}
</style>
