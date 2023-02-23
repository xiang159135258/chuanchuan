<template>
    <div>
        <DetailBanner></DetailBanner>
        <DetailHeader>1111111111111</DetailHeader>
        <div class="content"></div>
    </div>
</template>

<script>
import DetailBanner from './components/Banner.vue';
import DetailHeader from './components/Header.vue';
export default {
    name: 'Detail',
    components: {
        DetailBanner,
        DetailHeader
    }
}
</script>

<style lang="stylus" scoped>
    .content
        height: 1000px
</style>