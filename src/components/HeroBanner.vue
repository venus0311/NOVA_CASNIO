<template>
    <div class="hero-banner">
        <!-- Video Background -->
        <video 
            class="hero-video" 
            autoplay 
            muted 
            loop 
            playsinline
        >
            <source src="@/assets/img/banner.mp4" type="video/mp4">
            Your browser does not support the video tag.
        </video>
        
        <!-- Content Overlay -->
        <div class="hero-overlay">
            <div class="hero-content">
                <div class="hero-text">
                    <p class="hero-subtitle">Join and win big</p>
                    <h1 class="hero-title">
                        <span class="text-orange-gradient">Earn Referral</span> Bonus. 
                        The more people the more you earn
                    </h1>
                </div>
                
                <div class="hero-cta">
                    <div class="cta-card">
                        <h3>Refer & Earn Bonus</h3>
                        <div class="cta-coins">
                            <div class="cta-coin">$</div>
                            <div class="cta-coin">$</div>
                            <div class="cta-coin">$</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HeroBanner'
}
</script>

<style scoped>
.hero-banner {
    position: relative;
    border-radius: var(--radius-xl);
    margin: var(--spacing-xl);
    overflow: hidden;
    min-height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Video Background */
.hero-video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 1;
}

/* Overlay */
.hero-overlay {
    position: relative;
    z-index: 2;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.4);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: var(--spacing-2xl) var(--spacing-lg);
}

.hero-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: var(--spacing-2xl);
    width: 100%;
    max-width: 800px;
}

.hero-text {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
}

.hero-subtitle {
    font-size: 16px;
    color: #ffffff;
    font-weight: 500;
    margin: 0;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.7);
}

.hero-title {
    font-size: 48px;
    font-weight: 900;
    line-height: 1.2;
    margin: 0;
    color: #ffffff;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
}


/* CTA Card */
.hero-cta {
    position: relative;
    z-index: 5;
}

.cta-card {
    background: var(--gradient-orange);
    padding: var(--spacing-lg);
    border-radius: var(--radius-lg);
    text-align: center;
    box-shadow: var(--shadow-lg);
    min-width: 200px;
}

.cta-card h3 {
    color: white;
    font-size: 18px;
    font-weight: 700;
    margin: 0 0 var(--spacing-sm) 0;
}

.cta-coins {
    display: flex;
    justify-content: center;
    gap: var(--spacing-xs);
}

.cta-coin {
    width: 24px;
    height: 24px;
    background: rgba(255, 255, 255, 0.2);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    color: white;
    font-size: 12px;
}


@media only screen and (max-width: 1024px) {
    .hero-content {
        gap: var(--spacing-xl);
        text-align: center;
    }
    
    .hero-title {
        font-size: 36px;
    }
}

@media only screen and (max-width: 768px) {
    .hero-overlay {
        padding: var(--spacing-xl) var(--spacing-md);
    }
    
    .hero-banner {
        margin: var(--spacing-md);
    }
    
    .hero-title {
        font-size: 28px;
    }
    
    .cta-card {
        min-width: 150px;
        padding: var(--spacing-md);
    }
}
</style>
