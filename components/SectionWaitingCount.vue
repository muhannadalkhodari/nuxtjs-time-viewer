<template>
    <div class="d-flex flex-row darkBlueSlateBlue2 align-items-center px20">
        <div class="mr-0 ml-3">
            <img src="../assets/icons/arrow-right-white.svg" class="w18 arrow-icon"/>
        </div>
        <div class="mx-1 fw800">
            {{waitingList.length}}
        </div>
        <div class="mr-3 ml-2 fw800">
            {{messages.waitingList.ar}}
        </div>
    </div>
</template>

<script>
    import * as data  from "../assets/data/db.json";
    export default {
        setup() {
            const waitingList = data.waitingList;
            const messages = data.messages;

            return {
                waitingList,
                messages
            }
        }
    }
</script>

<style lang="scss" scoped>

    .w18 {
        width: 18px;
    }

    .arrow-icon {
        filter: invert(0.8) sepia(1) saturate(5) hue-rotate(180deg);
    }
</style>