<template>
    <div class="mx-5 my-5">
        
        <div class="row" dir="ltr">

            <div class="col-md-7 col-sm-12">
                <LazyComponentVideoPlayer :src="doctor.videos.about" />
            </div>

            <div class="col-md-5 col-sm-12" dir="rtl">
                <div class="row">
                    <div
                        v-for="item in doctor.products"
                        :key="item"
                        class="col-md-4 col-sm-6"
                    >
                        <LazyComponentProductThumbnail :item="item"/>
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
                messages: data.messages,
                doctor: data.doctor,
            }
        }
    }
</script>

<style lang="scss">
    .about-card {
        padding: 45px 28px;
        border-radius: 5px;
        box-shadow: 0 5px 86px 0 rgba(0, 0, 0, 0.05);
        max-height: 400px;
    }

    .experties-tags {
        line-height: 2.6;
    }

    .experties-tag {
        padding: 9px 31px;
        border-radius: 5px;
    }
</style>