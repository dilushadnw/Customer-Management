<template>
  <section class="hero-section">
    <div class="hero-background">
      <div class="animated-circle circle-1"></div>
      <div class="animated-circle circle-2"></div>
      <div class="animated-circle circle-3"></div>
    </div>

    <div class="hero-content container">
      <div class="hero-text">
        <h1 class="hero-title fade-in-up">
          Customer Management
          <span class="highlight">Made Simple</span>
        </h1>
        <p class="hero-subtitle fade-in-up" style="animation-delay: 0.2s">
          Streamline your customer relationships with our powerful, intuitive platform. Manage
          contacts, track interactions, and grow your business efficiently.
        </p>
        <div class="hero-buttons fade-in-up" style="animation-delay: 0.4s">
          <button class="btn btn-primary">
            <q-icon name="rocket_launch" size="20px" />
            Get Started
          </button>
          <button class="btn btn-secondary">
            <q-icon name="play_circle" size="20px" />
            Watch Demo
          </button>
        </div>
      </div>

      <div class="hero-stats">
        <div class="stat-item fade-in-up" style="animation-delay: 0.5s">
          <div class="stat-number">10K+</div>
          <div class="stat-label">Active Users</div>
        </div>
        <div class="stat-item fade-in-up" style="animation-delay: 0.6s">
          <div class="stat-number">99.9%</div>
          <div class="stat-label">Uptime</div>
        </div>
        <div class="stat-item fade-in-up" style="animation-delay: 0.7s">
          <div class="stat-number">24/7</div>
          <div class="stat-label">Support</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
//
</script>

<style scoped lang="scss">
.hero-section {
  position: relative;
  min-height: 90vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  background: var(--gradient-hero);
  color: var(--color-white);
  padding: var(--spacing-3xl) 0;
}

.hero-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: 0;
}

.animated-circle {
  position: absolute;
  border-radius: 50%;
  background: rgba(220, 38, 38, 0.1);
  animation: float 6s ease-in-out infinite;
}

.circle-1 {
  width: 300px;
  height: 300px;
  top: 10%;
  left: 10%;
  animation-delay: 0s;
}

.circle-2 {
  width: 200px;
  height: 200px;
  top: 60%;
  right: 15%;
  animation-delay: 2s;
}

.circle-3 {
  width: 150px;
  height: 150px;
  bottom: 20%;
  left: 50%;
  animation-delay: 4s;
}

.hero-content {
  position: relative;
  z-index: 1;
  text-align: center;
}

.hero-text {
  max-width: 800px;
  margin: 0 auto var(--spacing-3xl);
}

.hero-title {
  font-size: var(--text-6xl);
  font-weight: 800;
  margin-bottom: var(--spacing-lg);
  line-height: 1.1;

  @media (max-width: 768px) {
    font-size: var(--text-4xl);
  }
}

.highlight {
  display: block;
  background: linear-gradient(135deg, var(--color-red-primary), var(--color-red-secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-size: var(--text-xl);
  color: var(--color-gray-200);
  margin-bottom: var(--spacing-2xl);
  line-height: 1.8;

  @media (max-width: 768px) {
    font-size: var(--text-lg);
  }
}

.hero-buttons {
  display: flex;
  gap: var(--spacing-lg);
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: var(--spacing-sm);
  padding: var(--spacing-md) var(--spacing-xl);
  font-size: var(--text-lg);
  font-weight: 600;
  border-radius: var(--radius-xl);
  border: none;
  cursor: pointer;
  transition: all var(--transition-base) var(--ease-in-out);
  font-family: var(--font-primary);
}

.btn-primary {
  background: var(--gradient-red);
  color: var(--color-white);
  box-shadow: var(--shadow-red);

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 15px 40px -5px rgba(220, 38, 38, 0.5);
  }

  &:active {
    transform: translateY(-1px);
  }
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.1);
  color: var(--color-white);
  border: 2px solid var(--color-white);
  backdrop-filter: blur(10px);

  &:hover {
    background: var(--color-white);
    color: var(--color-black);
    transform: translateY(-3px);
  }

  &:active {
    transform: translateY(-1px);
  }
}

.hero-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: var(--spacing-2xl);
  max-width: 600px;
  margin: 0 auto;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: var(--text-4xl);
  font-weight: 800;
  color: var(--color-white);
  margin-bottom: var(--spacing-xs);
  font-family: var(--font-heading);
}

.stat-label {
  font-size: var(--text-sm);
  color: var(--color-gray-300);
  text-transform: uppercase;
  letter-spacing: 1px;
}

@media (max-width: 768px) {
  .hero-section {
    min-height: 80vh;
    padding: var(--spacing-2xl) 0;
  }

  .hero-stats {
    gap: var(--spacing-lg);
  }

  .stat-number {
    font-size: var(--text-3xl);
  }
}
</style>
