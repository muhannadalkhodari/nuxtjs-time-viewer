<template>
    <div>
        <video 
            :src="src"
            style="width: 100%"
        >

        </video>
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