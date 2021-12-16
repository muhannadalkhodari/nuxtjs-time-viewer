<template>
    <div 
        class="waiting-list-card container-fluid px-0
                darkBlueSlateBlue1 d-flex flex-column justify-content-between
                pr-5"
            v-if="waitingListOpened"
    >
        <div class="d-flex flex-column">
            <div class="d-flex flex-row px-4">
                <div class="mx-1 fw800" >
                    {{waitingList.length.toLocaleString('ar-EG')}}
                </div>

                <div class="mr-3 ml-2 fw800" >
                    {{messages.waitingList.ar}}
                </div>
            </div>

            <div class="small-line mx-4 mb-1"></div>

            <div class="waiting-users-list">
                <div 
                    v-for="user in waitingList" 
                    :key="user.id"
                >
                    <div 
                        class="d-flex flex-row py-3 px-3"
                        :class="{'me-card': user.id === me.id}"
                    >
                        <div class="d-flex ellipse justify-content-center align-items-center">
                            <img 
                                src="../assets/icons/user-bluegray.svg"
                                v-if="user.id !== me.id"
                            >
                            <img 
                                src="../assets/icons/user-secondary.svg"
                                v-else
                            >
                        </div>
                        <div class="d-flex flex-column justify-content-center mx-3">
                            <div class="px11 blueGreyLight">
                                {{messages.since.ar}}
                                {{user.waitingFrom.toLocaleString('ar-EG')}}
                                {{messages.minute.ar}}
                            </div>
                            <div class="fwBold px16">
                                {{user.name}}
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div 
            class="mr-3 ml-2 mb-3 px16 blueGreyLight2" 
        >
            <div class="d-flex flex-column">
                <div>
                    {{messages.rights.ar}}
                </div>

                <div class="mt-1">
                    {{messages.copyRights.ar}}
                    &copy;
                    {{(2013).toLocaleString('ar-EG', {useGrouping: false})}} -
                    {{(2021).toLocaleString('ar-EG', {useGrouping: false})}}
                </div>

                <div class="my-3">
                    <img src="../assets/icons/instagram.svg" class="ml-2 pointer"/>
                    <img src="../assets/icons/twitter.svg"  class="ml-2 pointer" />
                    <img src="../assets/icons/facebook.svg"  class="ml-2 pointer"/>
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
    import {ref} from "@nuxtjs/composition-api";
    import * as data  from "../assets/data/db.json";
    import moment  from "moment";

    export default {

        created() {
            this.$nuxt.$on('waitingListOpened', () => { setTimeout(() => {
                this.waitingListOpened = true;
            }, 600); });
            this.$nuxt.$on('waitingListClosed', () => { setTimeout(() => {
                this.waitingListOpened = false;
            }, 100); });
        },

        setup() {
            let waitingListOpened= ref(false);

            function toggle() {
                waitingListOpened.value = !waitingListOpened.value;
            }

            let waitingList = data.waitingList.map((uId, index) => {
                return {
                    id: uId,
                    name: data.users.find(u => u.id === uId)?.name,
                    waitingFrom: Math.round(moment.duration(moment().diff(moment().subtract((((data.waitingList.length-index)*5) - (Math.random()*4)), 'minutes'))).as('minutes'))
                }
            });

            return {
                toggle,
                me: data.me,
                waitingListOpened,
                sideNavOpened: false,
                waitingList,
                messages: data.messages,

            }
        }
    }
</script>

<style lang="scss" scoped>
    .waiting-list-card {
        width: 100%;
        height: 98.2vh;
        padding-top: 90px;
    }

    .small-line {
        width: 37px;
        height: 0;
        border: solid 2px #a7b5d2;
        margin: 16.5px 0 0 0;
    }

    .waiting-users-list {
        height: calc(83vh - 120px)  !important;
        overflow-y: scroll;
    }
    .waiting-users-list::-webkit-scrollbar {
        display: none;
    }

    .ellipse {
        width: 58px;
        height: 58px;
        object-fit: contain;
        box-shadow: -2px 2px 5px 0 rgba(0, 0, 0, 0.09);
        border: solid 1px #e9edf0;
        background-color: #fff;
        border-radius: 50%;
    }

    .me-card {
        background-color: #f5f5f5;
        border-radius: 0 50px 50px 0;
    }

</style>