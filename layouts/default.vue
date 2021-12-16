<template>
<div class="container-fluid px-0">
    <div class="d-flex flex-row">
        <div 
            class="flex-grow-1" 
            :class="{'left-shadow': waitingListOpened}"
        >
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
            :class="{'slide-in': waitingListOpened}"
            style="color: black"
        >
            <div>
                <LazySectionWaitingList />
            </div>
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
        background-color: white !important;
        width: 0px !important;
        transition: width 1s ease-in-out;
        height: 98.2vh;

        &.slide-in {
            width: 350px !important;
        }
    }

    .left-shadow {
        z-index: 100;
        box-shadow: -32px 140px 33px 0 rgb(29 66 139 / 51%);
    }
</style>