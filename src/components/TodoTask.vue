<template>
    <div :class="{before_icon : isPhotoBeforeIcon}">
        <div class="task card" v-if="!editMode" @click="editMode = true">
            <div class="task__number">{{index + 1}} </div>
            <div class="card__title task__title">{{task.title}}</div>
            <div class="card__desc task__desc">{{task.description}} </div>
        </div>
        <div class="task card" v-else>
            <div class="task__exit" @click="editMode = false">X</div> 
            <input class="card__input task__title" type="text" v-model="title"/>
            <textarea class="card__textarea task__desc" type="text" v-model="description" />
            <div class="task__buttons">
                <button class="button task__buttons--save" @click="editTask(index); editMode = false;">
                    <span class="button__text ">Save</span>
                </button>
                <button class="button task__buttons--remove" 
                @click="$emit('removeTask', index), editMode = false;">
                    <span class="button__text">Remove</span>
                </button>
            </div>
        </div>
    </div>
</template>

<script>

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
            editMode: false
        }
    },
    methods: {
        editTask(index){
            this.$emit('editTask', {
                title: this.title,
                description: this.description
            }, index);
        }
    },
    computed: {
        isPhotoBeforeIcon(){
            if(this.index < 2) return true; else return false;
        }
    }
}
</script>

<style lang="scss">
    @import "@/styles/layout/_task.scss";

    .before_icon{
        order: -1;
    }
</style>
