<template>
    <div class="d-flex flex-row darkBlueSlateBlue2 align-items-center">
        <div 
            class="mr-0 ml-3 pointer"
            :title="user.notifications"
        >
            <div 
                :class="{'notification-knob': user.notifications>0}"
            />
            <img src="../assets/icons/bell-white.svg" class="w27 bell-icon"/>
        </div>

        <div class="ellipse ml-0 mr-5 pointer">
            <img src="../assets/icons/profile.svg" class="w27 profile-icon"/>
        </div>
        <div class="mr-3 ml-2 fwBold px16">
            {{messages.welcome.ar}}
        </div>
        <div class="mx-1 fw800 px20">
            {{user.name}}
        </div>
    </div>
</template>

<script>
    import * as data  from "../assets/data/db.json";
    
    export default {
        setup() {
            const user = {
                ...data.me, 
                notifications: Math.random() >0.6? Math.round(Math.random()*10) : 0
            };
            const messages = data.messages;

            return {
                user,
                messages
            }
        }
    }
</script>

<style lang="scss" scoped>
    .ellipse {
        width: 45px;
        height: 45px;
        margin: 0 0 0 12px;
        padding: 9.3px 8.4px 8.4px 9.3px;
        object-fit: contain;
        box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.16);
        border: solid 2px #a7b5d2;
        background-color: #e9edf0;
        border-radius: 50%;
    }

    .w27 {
        width: 27px;
    }

    .bell-icon {
        filter: invert(0.8) sepia(1) saturate(5) hue-rotate(180deg);
    }

    .profile-icon {
        vertical-align: baseline;
        margin-top: -1.5px;
        margin-right: -1px;
    }

    .notification-knob {
        width: 16px;
        height: 16px;
        border-radius: 50%;
        margin: 0px -5px 0 0;
        z-index: 1000;
        position: absolute;
        border: solid 1.7px #1c3668;
        background-color: #e83866;
    }
</style>