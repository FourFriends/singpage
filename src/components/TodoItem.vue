<template>
  <li class='item' @click="handleAdd()">{{content}}</li>
</template>

<script>
  export default {
    props:['content','index'],
    methods:{
      handleAdd:function(){
        this.$emit('add',this.index)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  li.active{
    background: greenyellow;
  }
</style>
