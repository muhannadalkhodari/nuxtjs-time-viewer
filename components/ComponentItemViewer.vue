<template>
    <div class="row">
        <div class="col g-0 p-0">
            <video 
                :src="src"
                style="width: 98%"
            >

            </video>
        </div>
    </div>
</template>

<script>
    export default {
        props: [
            'src',
            'title'
        ]
    }
</script>

<style lang="scss" scoped>

</style>