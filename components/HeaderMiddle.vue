<template>
    <div style="background-color: white">
        <div 
            class="d-flex flex-row justify-content-between align-items-center header-middle darkBlueSlateBlue3BG
                    px-3 py-3 py-lg-5"
            :class="{'left-corner-round': waitingListOpened}"
        >
            <div class="d-block d-md-none">
                <LazySectionUser />
            </div>

            <div class="d-none d-md-block">
                <LazySectionExpertCard />
            </div>

            <LazySectionTimeViewerLogo />
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
                waitingListOpened
            }
        }
    }
</script>

<style lang="scss" scoped>
    .header-middle {
        // height: 183px;
        // padding: 48px 66px;
        opacity: 0.97;
        color: white;
        border-top-left-radius: 0px;
        // box-shadow: 0px 0px 0px 0 rgba(29, 66, 139, 0.51);
        transition: border-top-left-radius 1s, box-shadow 1s;
    }

    .left-corner-round {
        border-top-left-radius: 20px;
        // box-shadow: -32px 60px 33px 0 rgba(29, 66, 139, 0.51);
    }
</style>