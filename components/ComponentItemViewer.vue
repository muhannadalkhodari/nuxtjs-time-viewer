<template>
    <div class="d-flex flex-column mb-4 item-height">
        <div 
            class="thumbnail"
        >
            <div 
                class="d-flex flex-row justify-content-center hoverable"
            >
                <div 
                    class="thumbnail-light"
                    :class="{'darker': item.type !== 'video'}"
                ></div>

                <div v-if="item.type === 'video'"
                />

                <div class="d-flex flex-row g-0 align-items-center item-type-icon px25 fwBold blueGrey">
                    <div class="d-flex flex-column" dir="rtl">
                        <div class="d-flex flex-row">
                            <img v-if="item.type === 'video'" src="../assets/icons/video-cam-white.svg" />
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
                                <div class="px24 fwBold">
                                    {{item.price}}
                                </div>
                                <div class="mr-2 px16 fw500">
                                    {{messages.currency.ar}}
                                </div>
                            </div>
                        </div>

                        <div class="d-flex flex-row-reverse px14 blueGrey">
                            {{item.downloadCount}}
                            <img src="../assets/icons/downloads.svg" class="mr-2" />
                        </div>
                    </div>
                    
                </div>
            </div>
        </div>

        <!-- <div class="d-flex flex-column justify-content-between flex-grow-1">
            
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
    .item-height {
        max-height: 600px;
        height: 100%;
    }

    .thumbnail {
        background-color: #1d428b;
        height: 100%;
        border-radius: 5px;
        overflow: hidden;
    }

    .thumbnail-light {
        // background-image: linear-gradient(321deg, #10306f 86%, rgba(29, 66, 139, 0) 40%);
        background-image: linear-gradient(321deg, #10306fcc 5%, rgba(255,255,255, 0.3) 25%, rgba(29, 66, 139, 0));
        position: relative;
        width: 100%;
        height: 100%;

        &.darker {
            background-image: linear-gradient(321deg, #10306fcc 5%, rgba(29, 66, 139, 0));
        }
    }

    .item-type-icon {
        position: absolute;
        right: 30px;
        bottom: 120px;
    }
</style>