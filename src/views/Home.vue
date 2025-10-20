<template>
    <div class="home">
        <HeroBanner />
        <PopularGames />
        <LiveFeed />
    </div>
</template>

<script>
    import HeroBanner from '@/components/HeroBanner';
    import PopularGames from '@/components/PopularGames';
    import LiveFeed from '@/components/LiveFeed';

    export default {
        name: 'Home',
        metaInfo: {
            title: 'NOVA-CASINO: The Ultimate Gaming Experience'
        },
        components: {
            HeroBanner,
            PopularGames,
            LiveFeed
        }
    }
</script>

<style scoped>
    .home {
        width: 100%;
        min-height: calc(100vh - 80px);
        background: var(--bg-primary);
    }
</style>
