<template>
    <div 
        class="d-flex flex-row darkBlueSlateBlue2 align-items-center px20 hide-overflow pointer"
        @click="toggleWaitingList"
    >
        <!-- <div class="waiting-list-mobile-title d-none d-sm-block d-md-none"> -->
        <div 
            class="waiting-list-mobile-title d-block d-md-none "
            :class="{'move': waitingListOpened}"
        >
            <div class="d-flex flex-row px-4"
            >
                <div class="mx-1 fw800" >
                    {{waitingList.length.toLocaleString('ar-EG')}}
                </div>

                <div class="mr-3 ml-2 fw800" >
                    {{messages.waitingList.ar}}
                </div>
            </div>
        </div>

        <div 
            class="mr-0 ml-3 d-none d-md-block" 
        >
            <img 
                src="../assets/icons/arrow-right-white.svg" 
                class="w18 arrow-icon"
                :class="{'flip': waitingListOpened}"
            />
        </div>

        <div 
            class="d-flex flex-row card-to-hide" 
            :class="{'hide': waitingListOpened}"
        >
            <div 
                class="mx-1 fw800" 
            >
                {{waitingList.length.toLocaleString('ar-EG')}}
            </div>

            <div 
                class="mr-3 ml-2 fw800" 
            >
                {{messages.waitingList.ar}}
            </div>
        </div>

    </div>
</template>

<script>
    import {ref} from "@nuxtjs/composition-api";
    import * as data  from "../assets/data/db.json";

    export default {

        created() {
            this.$nuxt.$on('waitingListClosed', () => { setTimeout(() => {
                this.waitingListOpened = false;
            }, 100); });
        },

        setup() {
            let waitingListOpened= ref(false);

            function toggleWaitingList() {
                waitingListOpened.value = !waitingListOpened.value;

                if(waitingListOpened.value) {
                    $nuxt.$emit('waitingListOpened');
                }
                else {
                    $nuxt.$emit('waitingListClosed');
                }
            }

            const waitingList = data.waitingList;
            const messages = data.messages;

            return {
                toggleWaitingList,
                waitingListOpened,
                waitingList,
                messages
            }
        }
    }
</script>

<style lang="scss" scoped>
    .hide-overflow {
        overflow: hidden;
    }

    .w18 {
        width: 18px;
    }

    .arrow-icon {
        filter: invert(0.8) sepia(1) saturate(5) hue-rotate(180deg);

        transition: transform 1s;

        &.flip {
            transform: rotate(-180deg);
        }
    }

    .card-to-hide {
        transition: margin-left 0.5s, opacity 0.2s;

        &.hide {
            margin-left: -200px;
            opacity: 0;
        }
    }

    .waiting-list-mobile-title {
        position: absolute;
        top: 32px;
        right: 42px;
        transition: right 0.2s ease; // 0.2s;

        &.move {
            right: 25px;
        }
    }

</style>