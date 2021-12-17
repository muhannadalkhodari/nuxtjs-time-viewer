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

                <div class="d-block d-md-none">
                    <LazySectionMultimediaTests />
                </div>

                <div class="d-block d-md-none">
                    <div class="d-flex flex-row align-items-center p-4 m-0">
                        <LazySectionExpertCard />
                    </div>
                </div>

                <LazyHeaderExpert />
                
                <Nuxt/>

                <div class="reserve-mobile-card pointer d-block d-md-none">
                    <div class="d-flex flex-row justify-content-center align-items-center px16 fw800">
                        حجز عيادة (20 دينار كويتي)
                    </div>
                </div>
            </div>
        </div>
        <div 
            class="d-flex flex-column waiting-list"
            :class="{
                'slide-in-1000': waitingListOpened && ($nuxt.$route.path.length == 1),
                'slide-in-350': waitingListOpened && ($nuxt.$route.path.length > 1)
            }"
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

        &.slide-in-1000 {
            width: 1000px !important;
        }

        &.slide-in-350 {
            width: 350px !important;
        }
    }

    .left-shadow {
        z-index: 100;
        box-shadow: -32px 140px 33px 0 rgb(29 66 139 / 51%);
    }

    .reserve-mobile-card {
        position: fixed;
        margin: 0 10vw;
        bottom: 50px;
        height: 67px;
        width: 80vw;
        padding-top: 17px;
        border-radius: 10px;
        background-image: linear-gradient(107deg, #e83866 -26%, #e83866 -17%, #e57a3c 84%, #e57a3c 112%);
    }
</style>