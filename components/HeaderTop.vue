<template>
    <div>
        <div class="d-flex flex-row justify-content-between top-header darkBlueSlateBlue1">
            <LazySectionUser />
            <LazySectionWaitingCount />
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
                sideNavOpened: false
            }
        }
    }
</script>

<style lang="css" scoped>
    .top-header {  
        height: 93px;
        padding: 25px 66px;
    }
</style>