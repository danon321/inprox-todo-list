<template>
    <header class="header">
        <h1 class="header__title">{{title}}</h1>
        <h2 class="header__subtitle">{{subtitle}}</h2>
    </header>
</template>

<script>

export default {
    name: 'Header',
    props: {
        title: String,
        subtitle: String
    }
}
</script>


<style lang="scss" scoped>
    @import "@/styles/layout/_header.scss";
</style>