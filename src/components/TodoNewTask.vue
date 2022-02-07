<template>
    <div class="addtask__container">
        <div class="card addtask">
            <h3 class="card__title addtask__title">Tasks manager</h3>
            <input class="card__input addtask__input" type="text" v-model="title" placeholder="title">
            <textarea class="card__textarea addtask__textarea" v-model="description" placeholder="description"></textarea>  
            <button 
            class="button addtask__button" 
            :class="{disabled:disabled}"
            @click="addTask" 
            :disabled="disabled">
                <span class="button__text">Add Task</span>
            </button>
        </div>
        <div class="card addtask-bg-card">
            <img class="addtask-bg-card__img" :src="openTaskicon" alt="Open task icon">
            <span class="addtask-bg-card__text">Tasker</span>
        </div>
    </div>   
</template>

<script>
import openTaskicon from '@/assets/icons/Icon-open-task.svg'

export default {
    name: 'TodoNewTask',
    props:{
        disabled: Boolean
    },
    data(){
        return{
            title: '',
            description: '',
            openTaskicon
        }
    },
    methods: {
        addTask(){
            if(this.title == '') this.title = "No title";
            if(this.description == '') this.description = "No description";
            this.$emit('addTask', {
                title: this.title,
                description: this.description
            });

            this.title = '';
            this.description = '';
        }
    }
}
</script>

<style lang="scss" scoped>
    @import "@/styles/layout/_addtask.scss";
</style>
