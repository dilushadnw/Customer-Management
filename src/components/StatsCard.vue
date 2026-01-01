<template>
  <div class="stats-card" :class="`stats-card-${variant}`">
    <div class="stats-icon">
      <q-icon :name="icon" size="32px" />
    </div>
    <div class="stats-content">
      <div class="stats-value">{{ value }}</div>
      <div class="stats-label">{{ label }}</div>
      <div class="stats-change" :class="changeType">
        <q-icon :name="changeType === 'positive' ? 'trending_up' : 'trending_down'" size="16px" />
        {{ change }}
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  icon: {
    type: String,
    required: true,
  },
  value: {
    type: [String, Number],
    required: true,
  },
  label: {
    type: String,
    required: true,
  },
  change: {
    type: String,
    default: '',
  },
  changeType: {
    type: String,
    default: 'positive', // positive or negative
    validator: (value) => ['positive', 'negative'].includes(value),
  },
  variant: {
    type: String,
    default: 'red', // red, black, white
    validator: (value) => ['red', 'black', 'white'].includes(value),
  },
})
</script>

<style scoped lang="scss">
.stats-card {
  display: flex;
  align-items: center;
  gap: var(--spacing-lg);
  background: var(--color-white);
  border-radius: var(--radius-xl);
  padding: var(--spacing-xl);
  box-shadow: var(--shadow-md);
  transition: all var(--transition-base) var(--ease-in-out);
  border: 2px solid transparent;

  &:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-xl);
  }
}

.stats-card-red {
  border-color: var(--color-red-primary);

  .stats-icon {
    background: linear-gradient(135deg, var(--color-red-primary), var(--color-red-secondary));
    color: var(--color-white);
  }

  &:hover {
    box-shadow: var(--shadow-red);
  }
}

.stats-card-black {
  border-color: var(--color-black);

  .stats-icon {
    background: var(--gradient-dark);
    color: var(--color-white);
  }
}

.stats-card-white {
  border-color: var(--color-gray-300);

  .stats-icon {
    background: var(--color-gray-100);
    color: var(--color-red-primary);
  }
}

.stats-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 64px;
  height: 64px;
  border-radius: var(--radius-lg);
  flex-shrink: 0;
  transition: all var(--transition-base) var(--ease-in-out);
}

.stats-card:hover .stats-icon {
  transform: scale(1.1) rotate(-5deg);
}

.stats-content {
  flex: 1;
}

.stats-value {
  font-size: var(--text-3xl);
  font-weight: 800;
  color: var(--color-black);
  margin-bottom: var(--spacing-xs);
  font-family: var(--font-heading);
}

.stats-label {
  font-size: var(--text-sm);
  color: var(--color-gray-600);
  margin-bottom: var(--spacing-xs);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.stats-change {
  display: inline-flex;
  align-items: center;
  gap: var(--spacing-xs);
  font-size: var(--text-xs);
  font-weight: 600;
  padding: var(--spacing-xs) var(--spacing-sm);
  border-radius: var(--radius-full);

  &.positive {
    background: rgba(34, 197, 94, 0.1);
    color: #16a34a;
  }

  &.negative {
    background: rgba(239, 68, 68, 0.1);
    color: var(--color-red-primary);
  }
}

@media (max-width: 768px) {
  .stats-card {
    padding: var(--spacing-md);
    gap: var(--spacing-md);
  }

  .stats-icon {
    width: 48px;
    height: 48px;

    :deep(.q-icon) {
      font-size: 24px !important;
    }
  }

  .stats-value {
    font-size: var(--text-2xl);
  }

  .stats-label {
    font-size: var(--text-xs);
  }
}
</style>
