<template>
    <header class="header">
        <div class="header-container">
            <!-- Logo Section -->
            <div class="header-left">
                <router-link to="/" class="logo">
                    <div class="logo-icon">
                        <img src="@/assets/img/card_logo.png" alt="NOVA-CASINO Logo" />
                    </div>
                    <span class="logo-text">NOVA-CASINO</span>
                </router-link>
            </div>

            <!-- User Actions Section -->
            <div class="header-right">
                <button class="btn-signin" @click="showSignInModal = true">Sign In</button>
                <button class="btn-register" @click="showSignupModal = true">Register</button>
                <button class="btn-chat">
                    <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M18 5v8a2 2 0 01-2 2h-5l-5 4v-4H4a2 2 0 01-2-2V5a2 2 0 012-2h12a2 2 0 012 2z" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                </button>
            </div>
        </div>
        
        <!-- Signup Modal -->
        <SignupModal 
            :show="showSignupModal" 
            @close="showSignupModal = false" 
            @switch-to-signin="switchToSignIn" 
        />
        
        <!-- Sign In Modal -->
        <SignInModal 
            :show="showSignInModal" 
            @close="showSignInModal = false" 
            @switch-to-signup="switchToSignUp" 
        />
    </header>
</template>

<script>
import SignupModal from '@/components/SignupModal.vue';
import SignInModal from '@/components/SignInModal.vue';

export default {
    name: 'Header',
    components: {
        SignupModal,
        SignInModal
    },
    data() {
        return {
            showSignupModal: false,
            showSignInModal: false
        }
    },
    methods: {
        switchToSignIn() {
            this.showSignupModal = false;
            this.showSignInModal = true;
        },
        switchToSignUp() {
            this.showSignInModal = false;
            this.showSignupModal = true;
        }
    }
}
</script>

<style scoped>
.header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 80px;
    background: var(--bg-primary);
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    z-index: 100;
    display: flex;
    align-items: center;
}

.header-container {
    width: 100%;
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 var(--spacing-lg);
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.header-left {
    display: flex;
    align-items: center;
}

.logo {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
}

.logo-icon {
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.logo-icon img {
    width: 100%;
    height: 100%;
    object-fit: contain;
}

.logo-text {
    font-size: 24px;
    font-weight: 800;
    color: var(--text-primary);
    font-family: 'Inter', sans-serif;
}

.header-right {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
}

.btn-signin {
    padding: var(--spacing-sm) var(--spacing-lg);
    background: var(--bg-tertiary);
    color: var(--text-primary);
    border-radius: var(--radius-sm);
    font-weight: 600;
    font-size: 14px;
    transition: all 0.3s ease;
    border: 1px solid rgba(255, 255, 255, 0.1);
}

.btn-signin:hover {
    background: var(--bg-secondary);
    border-color: var(--accent-orange);
}

.btn-register {
    padding: var(--spacing-sm) var(--spacing-lg);
    background: var(--gradient-orange);
    color: white;
    border-radius: var(--radius-sm);
    font-weight: 600;
    font-size: 14px;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    position: relative;
    overflow: hidden;
    border: none;
    cursor: pointer;
}

.btn-register::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
    transition: left 0.5s ease;
}

.btn-register:hover {
    transform: scale(1.05);
    box-shadow: 
        0 10px 25px rgba(255, 107, 0, 0.4),
        0 5px 15px rgba(255, 107, 0, 0.2),
        0 0 0 1px rgba(255, 255, 255, 0.1);
    background: linear-gradient(135deg, #FF6B00 0%, #FF8A00 50%, #FFA500 100%);
}

.btn-register:hover::before {
    left: 100%;
}

.btn-register:active {
    transform: translateY(-1px) scale(1.02);
    transition: all 0.1s ease;
}

.btn-chat {
    width: 40px;
    height: 40px;
    background: var(--bg-tertiary);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--text-secondary);
    transition: all 0.3s ease;
    border: 1px solid rgba(255, 255, 255, 0.1);
}

.btn-chat:hover {
    background: var(--bg-secondary);
    color: var(--text-primary);
    transform: translateY(-2px);
}

@media only screen and (max-width: 768px) {
    .header-container {
        padding: 0 var(--spacing-md);
    }
    
    .logo-text {
        font-size: 20px;
    }
    
    .btn-signin,
    .btn-register {
        padding: var(--spacing-xs) var(--spacing-md);
        font-size: 12px;
    }
    
    .btn-chat {
        width: 36px;
        height: 36px;
    }
    
    .logo-icon {
        width: 28px;
        height: 28px;
    }
    
    .logo-icon img {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }
}

@media only screen and (max-width: 480px) {
    .header-right {
        gap: var(--spacing-sm);
    }
    
    .btn-signin {
        display: none;
    }
    
    .logo-text {
        font-size: 18px;
    }
}
</style>
