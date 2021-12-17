<template>
    <div class="row m-0 g-sm-1 g-md-3 mt-4" dir="ltr">

        <div class="col-sm-12 col-md-7">
            <!-- <LazyComponentItemViewer :item="selectedItem" /> -->
        </div>

        <div class="col-sm-12 col-md-5" dir="rtl">
            <div class="row px-2">
                <div
                    v-for="item in doctor.products"
                    :key="item"
                    class="col-6 col-md-6 col-lg-4 pointer"
                    @click="setSelectedItem(item)"
                >
                    <LazyComponentProductThumbnail :item="item"/>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
    import {ref} from "@nuxtjs/composition-api";
    import * as data  from "../assets/data/db.json";

    export default {
        setup() {

            let selectedItem = ref(data.doctor.products[0]);

            function setSelectedItem(item) {
                selectedItem.value = item;
            }

            return {
                selectedItem,
                setSelectedItem,
                messages: data.messages,
                doctor: data.doctor,
            }
        }
    }
</script>

<style lang="scss">

</style>