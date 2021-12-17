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
                    {{doctor.fullName}}

                    <div class="mr-4 mr-md-3 px13 white status-highlight px-3 py-1 mt-1">
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
</style>