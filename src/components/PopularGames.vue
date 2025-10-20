<template>
    <div class="popular-games">
        <h2 class="section-title">Popular Games</h2>
        <div class="games-grid">
            <div class="game-card" v-for="game in games" :key="game.id">
                <div class="game-screen" :class="{ 'casino-bg': game.id === 1, 'card2-bg': game.id === 2, 'card3-bg': game.id === 3, 'card4-bg': game.id === 4, 'card5-bg': game.id === 5 }">
                    <div class="title-curve">
                        <span class="card-title">{{ game.name }}</span>
                    </div>
                    <div class="game-info">
                        <h3 class="game-title">{{ game.name }}</h3>
                        <p class="game-subtitle">{{ game.subtitle }}</p>
                        <button class="play-button">Join Now</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PopularGames',
    data() {
        return {
            games: [
                {
                    id: 1,
                    name: 'Cases Battle',
                    subtitle: 'NOVA-CASINO Popular',
                    image: require('@/assets/img/chest.png')
                },
                {
                    id: 2,
                    name: 'Mines',
                    subtitle: 'RBXGOLD Original',
                    image: require('@/assets/img/mines/mine.png')
                },
                {
                    id: 3,
                    name: 'Cases Battle',
                    subtitle: 'NOVA-CASINO Popular',
                    image: require('@/assets/img/chest.png')
                },
                {
                    id: 4,
                    name: 'Mines',
                    subtitle: 'RBXGOLD Original',
                    image: require('@/assets/img/mines/mine.png')
                },
                {
                    id: 5,
                    name: 'Cases Battle',
                    subtitle: 'NOVA-CASINO Popular',
                    image: require('@/assets/img/chest.png')
                }
            ]
        }
    }
}
</script>

<style scoped>
.popular-games {
    padding: var(--spacing-2xl) var(--spacing-lg);
    background: var(--bg-primary);
}

.section-title {
    font-size: 32px;
    font-weight: 900;
    text-align: center;
    margin: 0 0 var(--spacing-2xl) 0;
}

.games-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: var(--spacing-lg);
    max-width: 1400px;
    margin: 0 auto;
}

.game-card {
    border-radius: 30px;
    padding: 6px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s ease;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    aspect-ratio: 9/16;
    display: flex;
    flex-direction: column;
}

.game-card:nth-child(1) {
    border: 2px solid #CC88E5;
}

.game-card:nth-child(2) {
    border: 2px solid #13C6FF;
}

.game-card:nth-child(3) {
    border: 2px solid #5BFFBB;
}

.game-card:nth-child(4) {
    border: 2px solid #7A8BFD;
}

.game-card:nth-child(5) {
    border: 2px solid #CC88E5;
}

.game-card:hover {
    transform: translateY(-8px);
    border-color: #5F9EA0;
    box-shadow: 0 8px 25px rgba(95, 158, 160, 0.3);
}

.game-screen {
    width: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
    background: #ffffff;
    border-radius: 25px;
    min-height: 0;
    padding: 20px;
}

.game-screen.casino-bg {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), 
                url('~@/assets/img/card_female.png');
    background-size: cover;
    background-position: center;
    color: white;
}

.game-screen.card2-bg {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), 
                url('~@/assets/img/card_2.png');
    background-size: cover;
    background-position: center;
    color: white;
}

.game-screen.card3-bg {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), 
                url('~@/assets/img/card_3.png');
    background-size: cover;
    background-position: center;
    color: white;
}

.game-screen.card4-bg {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), 
                url('~@/assets/img/card_4.jpg');
    background-size: cover;
    background-position: center;
    color: white;
}

.game-screen.card5-bg {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)), 
                url('~@/assets/img/card_5.jpg');
    background-size: cover;
    background-position: center;
    color: white;
}

.title-curve {
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    width: 140px;
    height: 40px;
    border-radius: 20px 20px 0 0;
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
}

.title-curve::after {
    content: '';
    position: absolute;
    bottom: 3px;
    left: 50%;
    transform: translateX(-50%);
    width: 141px;
    height: 25px;
    border-radius: 0 0 21px 21px;
    z-index: 1;
}

.game-card:nth-child(1) .title-curve::after {
    background: #CC88E5;
}

.game-card:nth-child(2) .title-curve::after {
    background: #13C6FF;
}

.game-card:nth-child(3) .title-curve::after {
    background: #5BFFBB;
}

.game-card:nth-child(4) .title-curve::after {
    background: #7A8BFD;
}

.game-card:nth-child(5) .title-curve::after {
    background: #CC88E5;
}

.card-title {
    font-size: 14px;
    font-weight: 700;
    text-align: center;
    position: relative;
    z-index: 3;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    max-width: 120px;
}



.game-info {
    text-align: center;
    padding: 10px;
    flex-shrink: 0;
    margin-top: auto;
}

.game-screen.casino-bg .game-info {
    color: white;
}

.game-screen.card2-bg .game-info {
    color: white;
}

.game-screen.card3-bg .game-info {
    color: white;
}

.game-screen.card4-bg .game-info {
    color: white;
}

.game-screen.card5-bg .game-info {
    color: white;
}

.game-title {
    font-size: 21px;
    font-weight: 700;
    color: #FFFFFF;
    margin: 0 0 4px 0;
}

.game-screen.casino-bg .game-title {
    color: white;
}

.game-subtitle {
    font-size: 12px;
    color: #2F4F4F;
    margin: 0 0 8px 0;
}

.game-screen.casino-bg .game-subtitle {
    color: rgba(255, 255, 255, 0.8);
}

.game-screen.card2-bg .game-title {
    color: white;
}

.game-screen.card2-bg .game-subtitle {
    color: rgba(255, 255, 255, 0.8);
}

.game-screen.card3-bg .game-title {
    color: white;
}

.game-screen.card3-bg .game-subtitle {
    color: rgba(255, 255, 255, 0.8);
}

.game-screen.card4-bg .game-title {
    color: white;
}

.game-screen.card4-bg .game-subtitle {
    color: rgba(255, 255, 255, 0.8);
}

.game-screen.card5-bg .game-title {
    color: white;
}

.game-screen.card5-bg .game-subtitle {
    color: rgba(255, 255, 255, 0.8);
}

.play-button {
    background: transparent;
    color: #2F4F4F;
    border: 1px solid #2F4F4F;
    padding: 6px 12px;
    border-radius: 8px;
    font-weight: 600;
    font-size: 12px;
    transition: all 0.3s ease;
    cursor: pointer;
    position: relative;
    overflow: hidden;
}

.game-screen.casino-bg .play-button {
    color: white;
    border-color: white;
}

.game-screen.card2-bg .play-button {
    color: white;
    border-color: white;
}

.game-screen.card3-bg .play-button {
    color: white;
    border-color: white;
}

.game-screen.card4-bg .play-button {
    color: white;
    border-color: white;
}

.game-screen.card5-bg .play-button {
    color: white;
    border-color: white;
}

.play-button::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(255deg, #2F4F4F 0%, #708090 100%);
    transition: left 0.3s ease;
    z-index: -1;
    border-radius: 6px;
}

.play-button:hover::before {
    left: 0;
}

.play-button:hover {
    color: white;
    border-color: var(--accent-pink);
    box-shadow: 0 0 20px rgba(255, 50, 210, 0.3);
    border-color: #2F4F4F;
    box-shadow: 0 0 20px rgba(47, 79, 79, 0.3);
}

/* Game-specific styling - First card has casino background */

@media only screen and (max-width: 1024px) {
    .games-grid {
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: var(--spacing-lg);
    }
    
    .section-title {
        font-size: 28px;
    }
}

@media only screen and (max-width: 768px) {
    .popular-games {
        padding: var(--spacing-xl) var(--spacing-md);
    }
    
    .games-grid {
        grid-template-columns: 1fr;
        gap: var(--spacing-md);
    }
    
    .section-title {
        font-size: 24px;
    }
    
    .game-card {
        padding: var(--spacing-lg);
    }
    
    .game-image {
        height: 100px;
    }
}
</style>
