<template>
    <div id="app">
        <index></index>
    </div>
</template>

<script>
    import Index from './index.vue';

    export default {
        name: 'app',
        components: {
            Index
        }
    };
</script>

<style>
    html, body {
        margin: 0;
        padding: 0;
    }
</style>
