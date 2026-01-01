<template>
  <q-page class="home-page">
    <!-- Hero Section -->
    <HeroSection />

    <!-- Features Section -->
    <section class="features-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title fade-in-up">Powerful Features</h2>
          <p class="section-subtitle fade-in-up" style="animation-delay: 0.1s">
            Everything you need to manage your customers effectively
          </p>
        </div>

        <div class="features-grid">
          <FeatureCard
            v-for="(feature, index) in features"
            :key="index"
            :icon="feature.icon"
            :title="feature.title"
            :description="feature.description"
            class="fade-in-up"
            :style="`animation-delay: ${0.1 * (index + 1)}s`"
          />
        </div>
      </div>
    </section>

    <!-- Statistics Dashboard Section -->
    <section class="stats-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title fade-in-up">Dashboard Overview</h2>
          <p class="section-subtitle fade-in-up" style="animation-delay: 0.1s">
            Real-time insights into your customer management
          </p>
        </div>

        <div class="stats-grid">
          <StatsCard
            v-for="(stat, index) in stats"
            :key="index"
            :icon="stat.icon"
            :value="stat.value"
            :label="stat.label"
            :change="stat.change"
            :changeType="stat.changeType"
            :variant="stat.variant"
            class="fade-in-up"
            :style="`animation-delay: ${0.1 * (index + 1)}s`"
          />
        </div>
      </div>
    </section>

    <!-- Call to Action Section -->
    <section class="cta-section">
      <div class="container">
        <div class="cta-content fade-in-up">
          <h2 class="cta-title">Ready to Transform Your Customer Management?</h2>
          <p class="cta-description">
            Join thousands of businesses already using our platform to streamline their operations
          </p>
          <div class="cta-buttons">
            <button class="btn btn-primary-cta">
              <q-icon name="rocket_launch" size="20px" />
              Start Free Trial
            </button>
            <button class="btn btn-secondary-cta">
              <q-icon name="contact_support" size="20px" />
              Contact Sales
            </button>
          </div>
        </div>
      </div>
    </section>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import HeroSection from 'components/HeroSection.vue'
import FeatureCard from 'components/FeatureCard.vue'
import StatsCard from 'components/StatsCard.vue'

const features = ref([
  {
    icon: 'groups',
    title: 'Customer Database Management',
    description:
      'Centralize all customer information in one secure, easily accessible database. Search, filter, and organize customer data effortlessly.',
  },
  {
    icon: 'contact_phone',
    title: 'Contact Information Tracking',
    description:
      'Keep track of all customer contact details, including emails, phone numbers, addresses, and social media profiles in one place.',
  },
  {
    icon: 'analytics',
    title: 'Customer Analytics & Reports',
    description:
      'Generate comprehensive reports and gain valuable insights into customer behavior, trends, and business performance metrics.',
  },
  {
    icon: 'chat',
    title: 'Communication History',
    description:
      'Maintain a complete record of all customer interactions, emails, calls, and meetings for better relationship management.',
  },
  {
    icon: 'task_alt',
    title: 'Task & Follow-up Management',
    description:
      'Never miss a follow-up with automated reminders, task scheduling, and deadline tracking for customer-related activities.',
  },
  {
    icon: 'category',
    title: 'Customer Segmentation',
    description:
      'Organize customers into targeted segments based on behavior, demographics, or custom criteria for personalized engagement.',
  },
])

const stats = ref([
  {
    icon: 'people',
    value: '2,547',
    label: 'Total Customers',
    change: '+12.5%',
    changeType: 'positive',
    variant: 'red',
  },
  {
    icon: 'trending_up',
    value: '1,234',
    label: 'Active This Month',
    change: '+8.2%',
    changeType: 'positive',
    variant: 'black',
  },
  {
    icon: 'mail',
    value: '856',
    label: 'Messages Sent',
    change: '+23.1%',
    changeType: 'positive',
    variant: 'white',
  },
  {
    icon: 'schedule',
    value: '42',
    label: 'Pending Tasks',
    change: '-5.3%',
    changeType: 'negative',
    variant: 'red',
  },
])
</script>

<style scoped lang="scss">
.home-page {
  background: var(--color-white);
}

// Features Section
.features-section {
  padding: var(--spacing-3xl) 0;
  background: var(--color-gray-50);
}

.section-header {
  text-align: center;
  margin-bottom: var(--spacing-3xl);
}

.section-title {
  font-size: var(--text-4xl);
  font-weight: 800;
  color: var(--color-black);
  margin-bottom: var(--spacing-md);
  font-family: var(--font-heading);
}

.section-subtitle {
  font-size: var(--text-lg);
  color: var(--color-gray-600);
  max-width: 600px;
  margin: 0 auto;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: var(--spacing-2xl);

  @media (max-width: 768px) {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
  }
}

// Stats Section
.stats-section {
  padding: var(--spacing-3xl) 0;
  background: var(--color-white);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--spacing-xl);

  @media (max-width: 768px) {
    grid-template-columns: 1fr;
    gap: var(--spacing-md);
  }
}

// CTA Section
.cta-section {
  padding: var(--spacing-3xl) 0;
  background: var(--gradient-dark);
  color: var(--color-white);
}

.cta-content {
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
}

.cta-title {
  font-size: var(--text-4xl);
  font-weight: 800;
  color: var(--color-white);
  margin-bottom: var(--spacing-lg);
  font-family: var(--font-heading);

  @media (max-width: 768px) {
    font-size: var(--text-3xl);
  }
}

.cta-description {
  font-size: var(--text-lg);
  color: var(--color-gray-300);
  margin-bottom: var(--spacing-2xl);
  line-height: 1.8;
}

.cta-buttons {
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

.btn-primary-cta {
  background: var(--gradient-red);
  color: var(--color-white);
  box-shadow: var(--shadow-red);

  &:hover {
    transform: translateY(-3px);
    box-shadow: 0 15px 40px -5px rgba(220, 38, 38, 0.5);
  }
}

.btn-secondary-cta {
  background: transparent;
  color: var(--color-white);
  border: 2px solid var(--color-white);

  &:hover {
    background: var(--color-white);
    color: var(--color-black);
    transform: translateY(-3px);
  }
}

@media (max-width: 768px) {
  .features-section,
  .stats-section,
  .cta-section {
    padding: var(--spacing-2xl) 0;
  }

  .section-header {
    margin-bottom: var(--spacing-2xl);
  }
}
</style>
