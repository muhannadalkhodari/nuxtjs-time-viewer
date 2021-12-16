<template>
    <div class="d-flex flex-column">
        
        <div class="d-flex flex-row align-items-center">

            <div>
                <img src="../assets/icons/home.svg"/>
            </div>
            
            <div>
                <img src="../assets/img/doctor.png" class="w64 mx-2"/>
            </div>

            <div class="d-flex flex-column justify-contents-center">

                <div class="px18">
                    {{messages.digitalClinic.ar}}
                </div>

                <div class="d-flex flex-row align-items-center px20 cloudyBlue">
                    {{messages.of.ar}}
                    {{messages.doctor.ar}}
                    {{doctor.name}}

                    <div class="mx-3 px13 white status-highlight px-3 py-1 mt-1">
                        {{messages.busy.ar}}
                    </div>
                </div>
            </div>
        </div>

        <div 
            class="d-flex flex-row align-items-center px13 cloudyBlue
                    mr-5 pr-5"
        >
            <div 
                v-for="index in doctor.rating" 
                :key="index"
                class="mr-1"
            >
                <img src="../assets/icons/star-highlighted.svg" />
            </div>
            <div 
                v-for="index in (4-doctor.rating)" 
                :key="index"
                class="mr-1"
            >
                <img src="../assets/icons/star.svg"/>
            </div>

            <div class="mx-2">
                {{messages.rating.ar}}
            </div>
        </div>
        
    </div>
</template>

<script>
    import * as data  from "../assets/data/db.json";
    
    export default {
        setup() {

            return {
                messages: data.messages,
                doctor: data.doctor
            }
        }
    }
</script>

<style lang="scss" scoped>
    .w64 {
        width: 64px;
    }

    .status-highlight {
        border-radius: 16px;
        background-image: linear-gradient(121deg, #e83866 -28%, #e83866 -21%, #e57a3c 55%, #e57a3c 75%);
    }

    .gradient {
        background-image: linear-gradient(121deg, #e83866 -28%, #e83866 -21%, #e57a3c 55%, #e57a3c 75%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
    }

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