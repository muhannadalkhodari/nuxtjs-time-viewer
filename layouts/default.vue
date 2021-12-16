<template>
<div class="container-fluid px-0">
    <div class="d-flex flex-column">
        <LazyHeaderTop />
        <LazyHeaderMiddle />
        <LazyHeaderExpert />

        <Nuxt/>
    </div>
</div>
</template>

<script>
    import {ref} from "@nuxtjs/composition-api";

    export default {

        setup() {
            let state= ref(false);

            function toggle() {
                state.value = !state.value;
            }

            return {
                toggle,
                state,
                waitListOpened: false,
                sideNavOpened: false,
                users: []
            }
        }
    }
</script>

<style scoped>
    
</style>