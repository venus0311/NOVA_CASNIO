<template>
    <div class="home">
        <HeroBanner />
        <PopularGames />
        <AllGames />
        <LiveFeed />
    </div>
</template>

<script>
    import HeroBanner from '@/components/HeroBanner';
    import PopularGames from '@/components/PopularGames';
    import AllGames from '@/components/AllGames';
    import LiveFeed from '@/components/LiveFeed';

    export default {
        name: 'Home',
        metaInfo: {
            title: 'NOVA-CASINO: The Ultimate Gaming Experience'
        },
        components: {
            HeroBanner,
            PopularGames,
            AllGames,
            LiveFeed
        }
    }
</script>

<style scoped>
    .home {
        width: 100%;
        min-height: calc(100vh - 80px);
        background: var(--bg-primary) url('~@/assets/img/main_bg.svg') no-repeat center center;
        background-size: cover;
        background-attachment: fixed;
    }
</style>
