<template>
    <div>
        <li v-bind:class="{unfinish:bUnFinish}">
            {{content}}
            &nbsp;&nbsp;&nbsp;
            <button @click="DeleteItem" >删除该任务</button>
            &nbsp;&nbsp;&nbsp;
            <button @click="FinishItem">切换任务状态</button>
        </li>
    </div>
</template>

<script>
    export default {
        props:['content','index'],
        data() {
            return {
                bUnFinish: true,
            }
        },
        methods:{
            DeleteItem:function(){
                this.$emit('delete',this.index)
            },
            FinishItem:function(){
                this.bUnFinish = !this.bUnFinish;
            },
        },
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    li.unfinish{
        background: red;
    }
    li.finish{
        background: green;
    }
</style>
