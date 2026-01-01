<template>
  <div class="feature-card">
    <div class="feature-icon">
      <q-icon :name="icon" size="40px" />
    </div>
    <h3 class="feature-title">{{ title }}</h3>
    <p class="feature-description">{{ description }}</p>
    <div class="feature-hover-effect"></div>
  </div>
</template>

<script setup>
defineProps({
  icon: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
})
</script>

<style scoped lang="scss">
.feature-card {
  position: relative;
  background: var(--color-white);
  border-radius: var(--radius-2xl);
  padding: var(--spacing-2xl);
  box-shadow: var(--shadow-lg);
  transition: all var(--transition-base) var(--ease-in-out);
  overflow: hidden;
  border: 1px solid var(--color-gray-200);
  cursor: pointer;

  &:hover {
    transform: translateY(-10px);
    box-shadow: var(--shadow-2xl);
    border-color: var(--color-red-primary);

    .feature-icon {
      background: var(--gradient-red);
      color: var(--color-white);
      transform: scale(1.1) rotate(5deg);
    }

    .feature-hover-effect {
      opacity: 1;
      transform: scale(1.5);
    }
  }
}

.feature-hover-effect {
  position: absolute;
  top: -50%;
  right: -50%;
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, rgba(220, 38, 38, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  opacity: 0;
  transition: all var(--transition-slow) var(--ease-in-out);
  pointer-events: none;
}

.feature-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 80px;
  height: 80px;
  background: var(--color-gray-100);
  color: var(--color-red-primary);
  border-radius: var(--radius-xl);
  margin-bottom: var(--spacing-lg);
  transition: all var(--transition-base) var(--ease-in-out);
}

.feature-title {
  font-size: var(--text-xl);
  font-weight: 700;
  color: var(--color-black);
  margin-bottom: var(--spacing-md);
  font-family: var(--font-heading);
}

.feature-description {
  font-size: var(--text-base);
  color: var(--color-gray-600);
  line-height: 1.7;
  margin: 0;
}

@media (max-width: 768px) {
  .feature-card {
    padding: var(--spacing-xl);
  }

  .feature-icon {
    width: 60px;
    height: 60px;

    :deep(.q-icon) {
      font-size: 30px !important;
    }
  }

  .feature-title {
    font-size: var(--text-lg);
  }

  .feature-description {
    font-size: var(--text-sm);
  }
}
</style>
