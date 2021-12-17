<template>
    <div class="gradient d-flex flex-column justify-content-center" dir="ltr">
        <div class="multi-media-card d-flex flex-row align-items-center justify-content-around px-5 px-md-0" dir=rtl>

            <div class="px-0 px-md-3 d-flex flex-row align-items-center">

                <div class="d-flex ellipse green-border justify-content-center align-items-center">
                    <img src="../assets/icons/voice.svg" />
                </div>

                <div class="d-flex flex-column justify-contents-center px-0 px-md-2">
                    <div class="px16 fwBold d-none d-md-block">
                        {{messages.media.audio.ar}}
                    </div>
                    <div class="px14 cloudyBlue d-none d-md-block">
                        {{messages.media.vGood.ar}}
                    </div>
                </div>
            </div>

            <div class="px-0 px-md-3 d-flex flex-row align-items-center">

                <div class="d-flex ellipse red-border justify-content-center align-items-center">
                    <img src="../assets/icons/video-cam.svg" />
                </div>

                <div class="d-flex flex-column justify-contents-center px-0 px-md-2">
                    <div class="px16 fwBold d-none d-md-block">
                        {{messages.media.camera.ar}}
                    </div>
                    <div class="px14 cloudyBlue d-none d-md-block">
                        {{messages.media.notTested.ar}}
                    </div>
                </div>
            </div>

            <div class="px-0 px-md-3 d-flex flex-row align-items-center">

                <div class="d-flex ellipse orange-border justify-content-center align-items-center">
                    <img src="../assets/icons/network.svg" />
                </div>

                <div class="d-flex flex-column justify-contents-center px-3 px-sm-2">
                    <div class="px16 fwBold">
                        {{messages.media.internetSpeed.ar}}
                    </div>
                    <div class="px14 cloudyBlue">
                        Mbps {{(36).toLocaleString('ar-Eg')}}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import * as data  from "../assets/data/db.json";
    
    export default {
        setup() {

            return {
                messages: data.messages
            }
        }
    }
</script>

<style lang="scss" scoped>
    .gradient {
        height: 92px;
        background-image: linear-gradient(80deg, #254176 11%, #1c3668 95%);
    }
    .multi-media-card {
        max-width: 700px;
    }

    // .media-card {
    //     margin-right: 20px;
    //     margin-left: 20px;
    // }

    .ellipse {
        width: 52px;
        height: 52px;
        object-fit: contain;
        box-shadow: 0 4px 6px 0 rgba(0, 0, 0, 0.16);
        border-radius: 50%;
        background-color: #fff;
    }

    .green-border {
        border: solid 3px #1dd950;
    }

    .red-border {
        border: solid 3px #e21956;
    }

    .orange-border {
        border: solid 3px #e28519;
    }
</style>