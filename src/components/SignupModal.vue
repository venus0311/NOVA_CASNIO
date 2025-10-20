<template>
    <div v-if="show" class="modal-overlay" @click="close">
        <div class="modal-container" @click.stop>
            <div class="modal-content">
                <!-- Left Panel - Branding -->
                <div class="modal-left">
                    <div class="brand-section">
                        <h1 class="brand-title">NOVA CASINO</h1>
                        <div class="brand-background">
                            <img src="@/assets/img/signup_bk.jpg" alt="Background" />
                        </div>
                    </div>
                    <div class="legal-text">
                        <p>
                            By accessing this site, I confirm that I am at least 18 years old and have read and agree with the 
                            <strong class="highlight-orange">Terms of Service</strong>. I also confirm that I have read the 
                            <strong class="highlight-orange">Privacy Policy</strong>, and fully accept the terms.
                        </p>
                    </div>
                </div>

                <!-- Right Panel - Signup Form -->
                <div class="modal-right">
                    <button class="close-button" @click="close">
                        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M18 6L6 18M6 6L18 18" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </button>

                    <div class="form-container">
                        <h2 class="form-title">Sign up</h2>

                        <form @submit.prevent="handleSignup" class="signup-form">
                            <div class="form-group">
                                <label for="username">User Name</label>
                                <input 
                                    id="username" 
                                    v-model="form.username" 
                                    type="text" 
                                    placeholder="Name" 
                                    required 
                                />
                            </div>

                            <div class="form-group">
                                <label for="email">Email Address</label>
                                <input 
                                    id="email" 
                                    v-model="form.email" 
                                    type="email" 
                                    placeholder="Email" 
                                    required 
                                />
                            </div>

                            <div class="form-group">
                                <label for="password">Password</label>
                                <input 
                                    id="password" 
                                    v-model="form.password" 
                                    type="password" 
                                    placeholder="Password" 
                                    required 
                                />
                            </div>

                            <div class="referral-section">
                                <button type="button" class="referral-toggle" @click="showReferral = !showReferral">
                                    Enter Referral Code (Optional) 
                                    <span class="arrow">{{ showReferral ? '▼' : '▶' }}</span>
                                </button>
                                <div v-if="showReferral" class="referral-input">
                                    <input 
                                        v-model="form.referralCode" 
                                        type="text" 
                                        placeholder="Referral Code" 
                                    />
                                </div>
                            </div>

                            <div class="checkbox-group">
                                <label class="checkbox-label">
                                    <input 
                                        v-model="form.agreeToTerms" 
                                        type="checkbox" 
                                        required 
                                    />
                                    <span class="checkmark"></span>
                                    I agree with <strong class="highlight-orange">Terms of Service</strong>, and confirm that I am at least 18 years old!
                                </label>
                            </div>

                            <button type="submit" class="signup-button" :disabled="!form.agreeToTerms">
                                Sign up
                            </button>
                        </form>

                        <div class="signin-link">
                            <p>Already have an account? <span class="highlight-orange" @click="switchToSignIn">Sign in</span></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SignupModal',
    props: {
        show: {
            type: Boolean,
            default: false
        }
    },
    data() {
        return {
            showReferral: false,
            form: {
                username: '',
                email: '',
                password: '',
                referralCode: '',
                agreeToTerms: false
            }
        }
    },
    methods: {
        close() {
            this.$emit('close');
        },
        handleSignup() {
            // Handle signup logic here
            console.log('Signup form submitted:', this.form);
            // You can emit an event to parent component or call an API
            this.$emit('signup', this.form);
            this.close();
        },
        switchToSignIn() {
            this.$emit('switch-to-signin');
        }
    }
}
</script>

<style scoped>
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    backdrop-filter: blur(5px);
}

.modal-container {
    background: var(--bg-secondary);
    border-radius: var(--radius-xl);
    overflow: hidden;
    max-width: 800px;
    width: 90%;
    max-height: 90vh;
    min-height: 600px;
    display: flex;
    box-shadow: var(--shadow-lg);
}

.modal-content {
    display: flex;
    width: 100%;
    min-height: 500px;
}

/* Left Panel - Branding */
.modal-left {
    flex: 1;
    background: linear-gradient(135deg, rgba(26, 26, 26, 0.9) 0%, rgba(33, 30, 43, 0.9) 100%);
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: var(--spacing-2xl);
}

.brand-section {
    /*position: relative; */
    z-index: 2;
    text-align: center;
}

.brand-title {
    font-size: 48px;
    font-weight: 900;
    color: white;
    margin: 0 0 var(--spacing-lg) 0;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
}


.brand-background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    opacity: 0.3;
}

.brand-background img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.legal-text {
    position: relative;
    z-index: 2;
    color: white;
    font-size: 14px;
    line-height: 1.6;
}

.highlight-orange {
    color: var(--accent-orange);
}

/* Right Panel - Form */
.modal-right {
    flex: 1;
    background: var(--bg-primary);
    padding: var(--spacing-2xl);
    position: relative;
}

.close-button {
    position: absolute;
    top: var(--spacing-lg);
    right: var(--spacing-lg);
    background: none;
    border: none;
    color: white;
    cursor: pointer;
    padding: var(--spacing-sm);
    border-radius: var(--radius-sm);
    transition: background-color 0.3s ease;
}

.close-button:hover {
    background: rgba(255, 255, 255, 0.1);
}

.form-container {
    max-width: 400px;
    margin: 0 auto;
    padding-bottom: var(--spacing-xl);
}

.form-title {
    font-size: 32px;
    font-weight: 700;
    color: white;
    margin: 0 0 var(--spacing-xl) 0;
}

.signup-form {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
}

.form-group label {
    color: white;
    font-weight: 600;
    font-size: 14px;
}

.form-group input {
    padding: var(--spacing-md);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: var(--radius-md);
    background: var(--bg-tertiary);
    color: white;
    font-size: 14px;
    transition: border-color 0.3s ease;
}

.form-group input:focus {
    outline: none;
    border-color: var(--accent-orange);
}

.form-group input::placeholder {
    color: var(--text-muted);
}

.referral-section {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
}

.referral-toggle {
    background: none;
    border: none;
    color: var(--accent-orange);
    text-align: left;
    cursor: pointer;
    padding: var(--spacing-sm) 0;
    font-size: 14px;
    display: flex;
    align-items: center;
    gap: var(--spacing-xs);
}

.arrow {
    font-size: 12px;
    transition: transform 0.3s ease;
}

.referral-input {
    margin-top: var(--spacing-sm);
}

.referral-input input {
    width: 100%;
    padding: var(--spacing-md);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: var(--radius-md);
    background: var(--bg-tertiary);
    color: white;
    font-size: 14px;
}

.checkbox-group {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-sm);
    margin-top: var(--spacing-md);
}

.checkbox-label {
    /* display: flex; */
    align-items: flex-start;
    gap: var(--spacing-sm);
    color: white;
    font-size: 14px;
    line-height: 1.5;
    cursor: pointer;
    text-align: left;
}

.checkbox-label input[type="checkbox"] {
    margin: 0;
    width: 18px;
    height: 18px;
    accent-color: var(--accent-orange);
}

.signup-button {
   /*padding: var(--spacing-lg); */
   
    background: var(--gradient-orange);
    border: none;
    border-radius: var(--radius-md);
    color: white;
    font-size: 16px;
    font-weight: 700;
    cursor: pointer;
    transition: transform 0.2s ease;
  /*  margin-top: var(--spacing-xl); */
    width: 100%;
}

.signup-button:hover:not(:disabled) {
    transform: translateY(-2px);
}

.signup-button:disabled {
    opacity: 0.6;
    cursor: not-allowed;
}

.signin-link {
    text-align: center;
    margin-top: var(--spacing-lg);
}

.signin-link p {
    color: white;
    font-size: 14px;
}

.signin-link .highlight-orange {
    cursor: pointer;
    text-decoration: underline;
}

.signin-link .highlight-orange:hover {
    color: var(--accent-pink);
}

/* Responsive Design */
@media only screen and (max-width: 768px) {
    .modal-container {
        width: 95%;
        margin: var(--spacing-md);
    }
    
    .modal-content {
        flex-direction: column;
        min-height: auto;
    }
    
    .modal-left {
        padding: var(--spacing-lg);
        min-height: 300px;
    }
    
    .brand-title {
        font-size: 36px;
    }
    
    
    .modal-right {
        padding: var(--spacing-lg);
    }
    
    .form-title {
        font-size: 24px;
    }
}

@media only screen and (max-width: 480px) {
    .modal-left {
        display: none;
    }
    
    .modal-right {
        flex: none;
    }
    
    .form-title {
        font-size: 20px;
    }
}
</style>
