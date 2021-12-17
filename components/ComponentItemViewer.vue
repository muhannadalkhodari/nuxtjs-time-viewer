<template>
    <div class="my-3 my-md-5 item">
        
        <div 
            class="thumbnail"
        >
            <div 
                class="thumbnail-light"
                :class="{'darker': item.type !== 'video'}"
            ></div>

            <div v-if="item.type === 'video'">
                <video 
                    src="https://videos-cloudflare.jwpsrv.com/61bc8729_aedfa8767ab84265324b322e856d1afb096ee796/content/conversions/aqnx1YDY/videos/B3OR7LJU-33252557.mp4"
                    controls
                >
                </video>
            </div>

            <div class="buy-cart" v-if="item.type !== 'video'">
                <div class="d-flex flex-row align-items-center px16 fwBold white">
                    <img src="../assets/icons/cart.svg" style="z-index: 10;" />
                    <img src="../assets/icons/cart-ellipse.svg" style="margin-left: -40px;"/>
                    <div class="mx-4">
                        تحميل / شراء
                    </div>
                </div>
            </div>

            <div class="item-type-icon px25 fwBold blueGrey">
                <div class="d-flex flex-column" dir="rtl">
                    <div class="d-flex flex-row">
                        <!-- <img v-if="item.type === 'video'" src="../assets/icons/video-cam-white.svg" /> -->
                        <img v-if="item.type === 'audio'" src="../assets/icons/audio.svg" />
                        <img v-if="item.type === 'word'" src="../assets/icons/word.svg" />
                        <span v-if="item.type === 'word'" class="px-2">WORD</span>
                        <img v-if="item.type === 'pdf'" src="../assets/icons/pdf.svg" />
                        <span v-if="item.type === 'pdf'" class="px-2">PDF</span>
                    </div>

                    <div class="d-flex flex-row px14 fwBold pt-2 px29 white" style="max-width: 450px">
                        {{item.title}}
                    </div>

                    <div class="d-flex flex-row align-items-center justify-content-between">
                        <div class="d-flex flex-row align-items-center blueGrey">
                            <div class="px24 fwBold" :class="{'hidden': item.type === 'video'}">
                                {{item.price}}
                            </div>
                            <div class="mr-2 px16 fw500" :class="{'hidden': item.type === 'video'}">
                                {{messages.currency.ar}}
                            </div>
                        </div>
                    </div>

                    <div class="d-flex flex-row-reverse align-items-center px21 blueGrey" :class="{'hidden': item.type === 'video'}">
                        <img src="../assets/icons/downloads.svg" class="mr-2" style="height: 25px"/>
                        {{item.downloadCount}}
                    </div>
                </div>
                
            </div>

        </div>

        <!-- <div class="d-flex flex-column justify-content-between flex-grow-1">
            "about": "https://videos-cloudflare.jwpsrv.com/61bc8729_aedfa8767ab84265324b322e856d1afb096ee796/content/conversions/aqnx1YDY/videos/B3OR7LJU-33252557.mp4"
            
        </div> -->
    </div>
</template>

<script>
    import * as data  from "../assets/data/db.json";

    export default {
        props: [
            'item'
        ],

        setup() {

            return {
                messages: data.messages
            }
        }
    }
</script>

<style lang="scss" scoped>
    .item {
        width: 100%;
        position: relative;
        width: 100%;
        padding-top: 56.25%; /* 16:9 Aspect Ratio */
        background-color: #1d428b;
        border-radius: 5px;
    }

    video {
        width: 100%;
    }

    .thumbnail {
        position:  absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
    }

    .hidden {
        opacity: 0;
        z-index: -10000;
    }

    .thumbnail-light {
        position:  absolute;
        // background-image: linear-gradient(321deg, #10306f 86%, rgba(29, 66, 139, 0) 40%);
        background-image: linear-gradient(321deg, #10306fcc 5%, rgba(255,255,255, 0.3) 25%, rgba(29, 66, 139, 0));
        width: 100%;
        height: 100%;

        &.darker {
            background-image: linear-gradient(321deg, #10306fcc 5%, rgba(29, 66, 139, 0));
        }
    }

    .item-type-icon {
        position: absolute;
        width: 92%;
        right: 30px;
        bottom: 30px;
    }

    .buy-cart {
        position: absolute;
        left: 40px;
        top: 40px;
    }
</style>