<template>
    <div class="" dir="ltr">
        
        <div class="row p-0 m-0">

            <div class="col-md-7 col-sm-12">
                <LazyComponentItemViewer :item="doctor.videos.about" />
            </div>

            <div class="col-md-5 col-sm-12 px-md-5 py-md-5" dir="rtl">
                <div class="about-card d-flex align-items-center lightNavyBlue px20">
                    <div class="about-content">
                        {{doctor.bio}}
                    </div>
                </div>

                <div class="d-none d-md-block">
                    <div class="mx-4 my-3 fw800">
                        {{messages.experties.ar}}
                    </div>
                    <div class="experties-tags">
                        <span
                            v-for="exp in doctor.experties"
                            :key="exp"
                            class="px14 ml-3 cloudyBlue darkBlueSlateBlue4BG experties-tag"
                        >
                            {{exp}}
                        </span>
                    </div>
                </div>

                
                <div class="d-block d-md-none d-flex flex-column">
                    <div class="d-flex flex-row px-4 py-3 fw800">
                        {{messages.experties.ar}}
                    </div>
                    <div class="d-flex flex-row mx-3 px-2">
                        <div class="row">
                            <span
                                v-for="exp in doctor.experties"
                                :key="exp"
                                class="col-5 m-2 px14 cloudyBlue darkBlueSlateBlue4BG experties-tag text-center"
                            >
                                {{exp}}
                            </span>
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
    .about-card {
        padding: 45px 28px;
        border-radius: 5px;
        box-shadow: 0 5px 86px 0 rgba(0, 0, 0, 0.05);
        height: 350px;

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