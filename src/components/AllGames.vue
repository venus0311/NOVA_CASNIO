<template>
    <div class="all-games">
        <h2 class="section-title">All Games</h2>
        <div class="games-grid">
            <div class="game-card" v-for="game in games" :key="game.id" @click="navigateToGame(game.route)">
                <div class="game-screen" :class="game.bgClass">
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
    name: 'AllGames',
    data() {
        return {
            games: [
                {
                    id: 1,
                    name: 'Crash',
                    subtitle: 'NOVA-CASINO Popular',
                    route: '/crash',
                    bgClass: 'casino-bg'
                },
                {
                    id: 2,
                    name: 'Mines',
                    subtitle: 'RBXGOLD Original',
                    route: '/mines',
                    bgClass: 'card2-bg'
                },
                {
                    id: 3,
                    name: 'Upgrader',
                    subtitle: 'NOVA-CASINO Popular',
                    route: '/upgrader',
                    bgClass: 'card3-bg'
                },
                {
                    id: 4,
                    name: 'Towers',
                    subtitle: 'RBXGOLD Original',
                    route: '/towers',
                    bgClass: 'card4-bg'
                },
                {
                    id: 5,
                    name: 'Blackjack',
                    subtitle: 'NOVA-CASINO Popular',
                    route: '/blackjack',
                    bgClass: 'card5-bg'
                },
                {
                    id: 6,
                    name: 'Duels',
                    subtitle: 'RBXGOLD Original',
                    route: '/duels',
                    bgClass: 'casino-bg'
                },
                {
                    id: 7,
                    name: 'Battles',
                    subtitle: 'NOVA-CASINO Popular',
                    route: '/battles',
                    bgClass: 'card2-bg'
                },
                {
                    id: 8,
                    name: 'Unbox',
                    subtitle: 'RBXGOLD Original',
                    route: '/unbox',
                    bgClass: 'card3-bg'
                },
                {
                    id: 9,
                    name: 'Roll',
                    subtitle: 'NOVA-CASINO Popular',
                    route: '/roll',
                    bgClass: 'card4-bg'
                }
            ]
        }
    },
    methods: {
        navigateToGame(route) {
            this.$router.push(route);
        }
    }
}
</script>

<style scoped>
.all-games {
    padding: var(--spacing-2xl) var(--spacing-lg);
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

.game-card:nth-child(6) {
    border: 2px solid #13C6FF;
}

.game-card:nth-child(7) {
    border: 2px solid #5BFFBB;
}

.game-card:nth-child(8) {
    border: 2px solid #7A8BFD;
}

.game-card:nth-child(9) {
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

.game-card:nth-child(6) .title-curve::after {
    background: #13C6FF;
}

.game-card:nth-child(7) .title-curve::after {
    background: #5BFFBB;
}

.game-card:nth-child(8) .title-curve::after {
    background: #7A8BFD;
}

.game-card:nth-child(9) .title-curve::after {
    background: #CC88E5;
}

.card-title {
    font-size: 14px;
    font-weight: 700;
    color: white;
    z-index: 3;
    position: relative;
}

.game-info {
    text-align: center;
    z-index: 2;
    position: relative;
}

.game-title {
    font-size: 24px;
    font-weight: 900;
    margin: 0 0 8px 0;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.game-subtitle {
    font-size: 14px;
    margin: 0 0 20px 0;
    opacity: 0.9;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.play-button {
    background: rgba(255, 255, 255, 0.2);
    border: 2px solid rgba(255, 255, 255, 0.3);
    border-radius: 25px;
    color: white;
    cursor: pointer;
    font-size: 16px;
    font-weight: 700;
    padding: 12px 24px;
    transition: all 0.3s ease;
    text-transform: uppercase;
    letter-spacing: 1px;
    backdrop-filter: blur(10px);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.play-button:hover {
    background: rgba(255, 255, 255, 0.3);
    border-color: rgba(255, 255, 255, 0.5);
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(15px);
}

@media (max-width: 768px) {
    .games-grid {
        grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
        gap: var(--spacing-md);
    }
    
    .section-title {
        font-size: 24px;
    }
    
    .game-title {
        font-size: 18px;
    }
    
    .play-button {
        font-size: 12px;
        padding: 8px 16px;
    }
}
</style>
