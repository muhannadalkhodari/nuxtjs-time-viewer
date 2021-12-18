<template>
    <div class="row mx-0 mx-md-5" dir="ltr">

        <div 
            class="row m-0 mt-5" 
            dir="rtl"
            v-if="selectedItem == null"
        >
            <div
                v-for="item in courses"
                :key="item"
                class="col-12 col-md-4 col-lg-3 px-0 px-md-2 pointer"
                @click="setSelectedItem(item)"
            >
                <LazyComponentProductThumbnail :item="item"/>
            </div>
        </div>

        <div 
            class="row mt-5" 
            dir="rtl"
            v-if="selectedItem != null"
        >
            <LazyComponentCourseDetails :item="selectedItem"/>
        </div>

    </div>
</template>

<script>
    import {ref} from "@nuxtjs/composition-api";
    import * as data  from "../assets/data/db.json";

    export default {

        created() {
            this.$nuxt.$on('courseDeselected', () => {
                this.selectedItem = null;
            });
        },

        setup() {

            let selectedItem = ref(null);

            let courses = data.doctor.products.filter(i => i.type === 'video').map(item => {
                return {
                    ...item,
                    "course": true
                }
            });

            courses.push(...courses);

            function setSelectedItem(item) {
                selectedItem.value = item;
                $nuxt.$emit('courseSelected');
            }

            return {
                courses,
                selectedItem,
                setSelectedItem,
                messages: data.messages
            }
        }
    }
</script>

<style lang="scss">

</style>