<template>
    <main-header></main-header>
    <the-resources></the-resources>
</template>

<script>
import MainHeader from './components/UI/MainHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';
export default {
    components: {
        MainHeader,
        TheResources
    },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

</style>