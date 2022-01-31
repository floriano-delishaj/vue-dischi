<template>
    <main>
        <div class="container">
            <div class="row pt-5">
                <disk-card v-for="(disk,i) in discs" :key="i" :disk="disk"/>
            </div>
        </div>

    </main>
</template>

<script>

    import DiskCard from './DiskCard.vue'

    export default {
        components: {
            DiskCard
        },
        props: {
            discs: Array
        }
    }
</script>

<style lang="scss" scoped>

    @import '@/style/mainContainer.scss';

</style>