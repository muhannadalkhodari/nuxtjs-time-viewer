<template>
    <div class="d-flex flex-column mb-4 h280px"
        :class="{'course': item.course}"
    >
        <div 
            class="thumbnail"
            :style="{ 
                'background-image': item.type === 'video'? 
                    'url(' + require(`/assets/img/product-${Math.round(1+Math.random()*3)}.jpg`) + ')'
                    :'',
                'background-position': item.type === 'video'? 'center':''
            }" 
        >
            <div 
                class="d-flex flex-row justify-content-center hoverable"
            >
                <div 
                    class="thumbnail-light"
                    :class="{'darker': item.type !== 'video'}"
                ></div>

                <div class="d-flex flex-row g-0 align-items-center item-type-icon px19 fwBold blueGrey"
                    :class="{'course': item.course}"
                >
                    <span v-if="(item.type === 'video') && (item.course)" class="px-2 px14">
                        {{Math.round(Math.random() * 20 + 5)}}
                        {{messages.video.ar}}
                    </span>
                    <img v-if="(item.type === 'video') && (!item.course)" src="../assets/icons/video-cam-white.svg" />
                    <img v-if="(item.type === 'video') && (item.course)" src="../assets/icons/video-cam-secondary.svg" />
                    <img v-if="item.type === 'audio'" src="../assets/icons/audio.svg" />
                    <img v-if="item.type === 'word'" src="../assets/icons/word.svg" />
                    <span v-if="item.type === 'word'" class="px-2">WORD</span>
                    <img v-if="item.type === 'pdf'" src="../assets/icons/pdf.svg" />
                    <span v-if="item.type === 'pdf'" class="px-2">PDF</span>
                </div>
            </div>
        </div>

        <div class="d-flex flex-column justify-content-between flex-grow-1">
            <div class="px14 fwBold pt-2">
                {{item.title}}
            </div>

            <div class="d-flex flex-row align-items-center justify-content-between">
                <div class="d-flex flex-row align-items-center blueGrey">
                    <div class="px19 fwBold">
                        {{item.price}}
                    </div>
                    <div class="mr-2 px13 fw500">
                        {{messages.currency.ar}}
                    </div>
                </div>

                <div class="d-flex flex-row align-items-center px14 blueGrey" v-if="(!item.course)" >
                    {{item.downloadCount}}
                    <img src="../assets/icons/downloads.svg" class="mr-2" />
                </div>
            </div>
        </div>
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
    .h280px {
        height: 280px !important;

        &.course{
            height: 260px !important;
        }
    }

    .thumbnail {
        background-color: #1d428b;
        height: 196px;
        border-radius: 5px;
        overflow: hidden;
    }

    .thumbnail-light {
        // background-image: linear-gradient(321deg, #10306f 86%, rgba(29, 66, 139, 0) 40%);
        background-image: linear-gradient(321deg, #10306fcc 5%, rgba(255,255,255, 0.3) 25%, rgba(29, 66, 139, 0));
        position: relative;
        width: 100%;
        height: 196px;

        &.darker {
            background-image: linear-gradient(321deg, #10306fcc 5%, rgba(29, 66, 139, 0));
        }
    }

    .item-type-icon {
        position: absolute;
        right: 30px;
        bottom: 120px;

        &.course{
            bottom: 100px;
        }
    }
</style>