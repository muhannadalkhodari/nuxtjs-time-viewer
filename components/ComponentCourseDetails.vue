<template>
    <div class="" dir="ltr">
        
        <div class="row p-0 m-0">

            <div class="col-md-7 col-sm-12">
                <LazyComponentItemViewer :item="doctor.products[0]" />
            </div>

            <div class="col-md-5 col-sm-12 px-0 px-md-5 py-md-5" dir="rtl">

                <div class="d-flex flex-column">

                    <div class="course-about-card lightNavyBlue px20">
                        <div class="d-flex flex-column">
                            <div class="px29 fw800 white m-2">
                                {{messages.courseDescription.ar}}
                            </div>
                            <div class="about-content px24 m-2">
                                {{messages.loremIpsum.ar}}
                            </div>
                        </div>
                    </div>

                    <div class="row mt-4" dir="rtl">
                        <div class="row mx-5 mx-lg-0 px-0 px-lg-3">
                            <div
                                v-for="item in doctor.products.filter(i => i.type === 'video')"
                                :key="item"
                                class="col-6 col-md-12 col-lg-4 pointer"
                            >
                                <LazyComponentProductThumbnail :item="item"/>
                            </div>
                        </div>
                    </div>

                    <div class="mx-4 px25 fw800 cloudyBlue">
                        {{doctor.products.filter(i => i.type === 'video')[2].title}}
                    </div>

                    <div class="row mt-4" dir="rtl">
                        <div class="row mx-5 mx-lg-0 px-0 px-lg-3">
                            <div
                                v-for="item in doctor.products.filter(i => i.type === 'video')"
                                :key="item"
                                class="col-6 col-md-12 col-lg-4 pointer"
                            >
                                <LazyComponentProductThumbnail :item="item"/>
                            </div>
                        </div>
                    </div>

                    <div class="mx-4 px25 fw800 cloudyBlue">
                        {{doctor.products.filter(i => i.type === 'video')[2].title}}
                    </div>

                    <div class="row mt-4" dir="rtl">
                        <div class="row mx-5 mx-lg-0 px-0 px-lg-3">
                            <div
                                v-for="item in doctor.products.filter(i => i.type === 'video')"
                                :key="item"
                                class="col-6 col-md-12 col-lg-4 pointer"
                            >
                                <LazyComponentProductThumbnail :item="item"/>
                            </div>
                        </div>
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
                doctor: data.doctor
            }
        }
    }
</script>

<style lang="scss">
    .course-about-card {
        padding: 45px 28px;
        border-radius: 5px;
        box-shadow: 0 5px 86px 0 rgba(0, 0, 0, 0.05);
        height: 450px;

        .about-content {
            max-height: 300px;
            overflow-y: scroll;
        }

        .about-content::-webkit-scrollbar {
            display: none;
        }
    }

    .experties-tags {
        line-height: 2.6;
    }

    .experties-tag {
        padding: 9px 31px;
        border-radius: 5px;
    }
</style>