<template>
    <div class="todolist">
        <TodoNewTask 
        @addTask="addTask" 
        :disabled="(tasks.length >= 5) ? true : false" />

        <div class="tasks">
            <TodoTask
            :task="task" 
            :index="index" 
            v-for="(task, index) in tasks" 
            :key="index"
            @removeTask="removeTask"
            @editTask="editTask" />

            <div class="icon">
                <img class="icon__img icon__img--tasks" :src="taskIcon" alt="Task Icon">
            </div>
        </div>
    </div>
</template>

<script>
import TodoNewTask from '@/components/TodoNewTask.vue';
import TodoTask from '@/components/TodoTask.vue';
import taskIcon from '@/assets/icons/tasks-icon.svg';

export default {
    name: 'TodoList',
    components: {
        TodoNewTask,
        TodoTask
    },
    data(){
        return{
            tasks:[],
            taskIcon: taskIcon
        }
    },
    methods:{
        addTask(e){
            this.tasks.push(e);
        },
        removeTask(index){
            this.tasks.splice(index, 1);
        },
        editTask(updatedTask,index){
            for(let propertie in updatedTask)
                this.tasks[index][propertie] = updatedTask[propertie];
        }
    }
}
</script>

<style lang="scss" scoped>
    @import "@/styles/layout/_todolist.scss";
    @import "@/styles/components/_icon.scss";
</style>
