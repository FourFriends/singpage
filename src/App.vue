<template>
  <div>
  <h2>一、你现在可以做下面的事情</h2>
    <ol>
      <todo-item
              v-for="(item,index) of todolist"
              :key="index"
              :content="item"
              :index="index"
              @add="HandleAdd"
      ></todo-item>
    </ol>
  <h2>二、直接在上面点击，选择你将要做的事情</h2>
    <ol>
      <li  v-for="(item,index) of selectList" :key="index">{{item}}</li>
    </ol>
  </div>
</template>

<script>
  import TodoItem from "./components/TodoItem"
  export default {
    components:{
      'todo-item':TodoItem,
    },
    data(){
    return{
      todolist:["吃饭","睡觉","打豆豆","聊QQ","聊微信"],
      selectList:[],
      current:""//当前选中的index
    }
  },
    methods:{
      HandleAdd(index){
        this.selectList.push(this.todolist[index])
      }
    }
}
</script>

<style>

</style>
