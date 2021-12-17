<template>
    <div>
        <div class="d-flex flex-row justify-content-between top-header darkBlueSlateBlue1">
            <div class="d-none d-md-block">
                <LazySectionUser />
            </div>

            <LazySectionWaitingCount />

            <div 
                class="d-block d-md-none pointer"
                @click="navToggle"
            >
                <img src="../assets/icons/nav-menu.svg" alt="">
            </div>

            <div 
                class="nav-manu"
                :class="{'nav-manu-opened':navState}"
            >
                <div 
                    class="d-flex flex-column align-items-center justify-content-around py-5" 
                    style="height: 100%; color: #1d428b"
                >
                    <div 
                        v-for="(item, index) in navItems" 
                        :key="index"
                        class="px17 fw500"
                        :class="{'fwBold':index == 0 || index == navItems.length-1}"
                    >
                        <div class="pointer">
                            {{item}}
                        </div>
                    </div>
                    
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import {ref} from "@nuxtjs/composition-api";

    export default {

        setup() {
            let state= ref(false);
            let navState= ref(false);

            function toggle() {
                state.value = !state.value;
            }

            function navToggle() {
                navState.value = !navState.value;
            }

            let navItems = [
                "الرئيسية",
                "نبذه عنا",
                "الخبراء",
                "سؤال وجواب",
                "اختبارات كورونا",
                "اتصل بنا",
                "انضم كخبير",
            ]

            return {
                toggle,
                state,
                navState,
                navToggle,
                navItems,
                waitListOpened: false,
                sideNavOpened: false
            }
        }
    }
</script>

<style lang="scss" scoped>
    .top-header {  
        height: 93px;
        padding: 25px 66px;
        background-color: white;
    }

    .nav-manu {
        position: fixed;
        z-index: 10000;
        left: -500px;
        top: 93px;
        height: calc(100vh - 93px);
        width: 500px;
        background: rgb(250, 250, 250);
        box-shadow: inset 0px 5px 5px #ebebeb;
        transition: left 0.5s ease-in-out;

        &.nav-manu-opened {
            left: 0;
        }
    }
</style>