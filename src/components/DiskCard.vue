<template>
    <div class="col-2 mr-2 mb-3">
        <div class="text-center">
            <div class="disk-card">
                <img :src="disk.poster" alt="">
                <h6 class="text-white pt-2">{{disk.title}}</h6>
                <p>{{disk.author}}</p>
                <p>{{disk.year}}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            disk: Object
        }
    }
</script>

<style lang="scss" scoped>

    @import '@/style/diskCard.scss';

</style>