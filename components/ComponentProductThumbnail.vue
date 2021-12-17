<template>
    <div class="d-flex flex-column mb-4 h280px">
        <div class="thumbnail-light">
            <div 
                class="thumbnail d-flex flex-row justify-content-center"
            >
                <!-- <img src="../assets/img/product-1.jpg" class="clip"> -->
                <img :src="require(`/assets/img/product-${Math.round(1+Math.random()*3)}.jpg`)">
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

                <div class="d-flex flex-row align-items-center px14 blueGrey">
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
    }

    .thumbnail {
        height: 200px;
        object-fit: contain;
        border-radius: 5px;
        background-color: #1d428b;
        overflow: hidden;
    }

    .thumbnail-light {
        // background-image: linear-gradient(321deg, #10306f 86%, rgba(29, 66, 139, 0) 40%);
        background-image: linear-gradient(321deg, #10306fcc 5%, rgba(255,255,255, 0.3) 25%, rgba(29, 66, 139, 0));
    }
</style>