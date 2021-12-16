<template>
<div class="container-fluid px-0">
    <div class="d-flex flex-row">
        <div class="flex-grow-1">
            <div 
                class="d-flex flex-column"                
            >
                <LazyHeaderTop />
                <LazyHeaderMiddle />
                <LazyHeaderExpert />

                <Nuxt/>
            </div>
        </div>
        <div 
            class="d-flex flex-column waiting-list"
            :class="{'slide-in': !waitingListOpened}"
            style="color: black"
        >
            Waiting List Section
        </div>
    </div>
</div>
</template>

<script>
    import {ref} from "@nuxtjs/composition-api";

    export default {

        created() {
            this.$nuxt.$on('waitingListOpened', () => { this.toggle() });
            this.$nuxt.$on('waitingListClosed', () => { this.toggle() });
        },

        setup() {
            let waitingListOpened= ref(false);

            function toggle() {
                waitingListOpened.value = !waitingListOpened.value;
            }

            return {
                toggle,
                waitingListOpened,
                sideNavOpened: false,
                users: []
            }
        }
    }
</script>

<style lang="scss" scoped>
    .waiting-list {
        width: 0px;
        transition: width 1s ease-in-out;

        &.slide-in {
            width: 350px;
        }
    }
</style>