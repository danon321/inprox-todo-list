<template>
    <div class="blob-wrap" :class="createClassByPosition">
        <div class="blob"></div>
    </div>
</template>

<script>
export default {
    name: 'Blob',
    props: {
        position: {
            type: String,
            required: true
        }
    },
    computed:{
        createClassByPosition(){
            return `blob--${this.position}`;
        }
    }
}
</script>

<style lang="scss" scoped>
    @import "@/styles/components/_blob.scss";
</style>