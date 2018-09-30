<template>
    <div class="container">
        <h1>Site</h1>
        <div>Hello, {{ name }}</div>
        <hr>
    </div>
</template>

<script>
    import {mapGetters} from 'vuex';

    export default {
        computed: {
            ...mapGetters([
                'name'
            ])
        }
        
    }
</script>

