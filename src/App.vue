<template>
  <div>
  <h2>一、请增加你的日程或者从下面进行选择：</h2>
    <p>请选择日期：<input type="date" v-model="date"/></p>
    <p>
      请输入你计划做的事情：<input type="text" v-model="msg"/>
      &nbsp;&nbsp;
      <button type="button" @click="AddList">提交</button>
    </p>

    <ol>
      <handle-add
              v-for="(item,index) of todolist"
              :key="index"
              :content="item"
              :index="index"
              @add="HandleAdd"
      ></handle-add>
    </ol>
  <h2>二、直接在上面点击，选择你将要做的事情</h2>
    <ol>
        <handle-delete
                v-for="(item,index) of selectList"
                :key="index"
                :content="item"
                :index="index"
                @delete="HandleDelete"
        ></handle-delete>
    </ol>
  </div>
</template>

<script>
  import HandleAdd from "./components/HandleAdd"
  import HandleDelete from "./components/HandleDelete"
  export default {
    components:{
      'handle-add':HandleAdd,
      'handle-delete':HandleDelete,
    },
    data(){
    return{
      todolist:[],
      selectList:[],
      msg:"",
      date:"2019-05-23"
    }
  },
    methods:{
      HandleAdd(index){
        var str = this.date + " " + this.todolist[index];
        this.selectList.push(str);
      },
      AddList()
      {
        if(this.msg === '') return;
        var str = this.date + " " + this.msg;
        this.selectList.push(str);
        this.msg = '';
      },
      HandleDelete(index){
          this.selectList.splice(index,1);
      },
    }
}
</script>

<style>

</style>
