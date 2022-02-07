<template>
    <div>
        <div class="task card" v-if="!editMode" @click="editMode = true">
            <div class="task__number">{{index + 1}} </div>
            <div class="task__content">
                <div class="card__title task__title">{{task.title}}</div>
                <div class="card__desc task__desc">{{task.description}} </div>
            </div>
        </div>
        <div class="task card" v-else>
            <div class="task__exit" @click="editMode = false">X</div> 
            <div class="task__content">
                <input class="card__input task__title" type="text" v-model="title"/>
                <textarea class="card__textarea task__desc" type="text" v-model="description" />
                <div class="task__buttons">
                    <button class="button task__buttons--remove" 
                    @click="$emit('removeTask', index), editMode = false;">
                        <span class="button__text">Remove</span>
                    </button>
                    <button class="button task__buttons--save" @click="editTask(index); editMode = false;">
                        <img :src="saveIcon" width="20" alt="Ok - icon">
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import saveIcon from '@/assets/icons/save-icon.svg';

export default {
    name: 'TodoTask',
    props:{
        task: Object,
        index: Number
    },
    data(){
        return{
            title: this.task.title,
            description: this.task.description,
            editMode: false,
            saveIcon
        }
    },
    methods: {
        editTask(index){
            this.$emit('editTask', {
                title: this.title,
                description: this.description
            }, index);
        }
    }
}
</script>

<style lang="scss">
    @import "@/styles/layout/_task.scss";
</style>
