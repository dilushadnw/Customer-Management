<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="custom-header">
      <q-toolbar class="custom-toolbar">
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
          class="menu-btn"
        />

        <q-toolbar-title class="brand-title">
          <q-icon name="business_center" size="28px" class="brand-icon" />
          <span class="brand-text">CustomerHub</span>
        </q-toolbar-title>

        <div class="header-actions">
          <q-btn flat round dense icon="notifications" class="action-btn">
            <q-badge color="red" floating>3</q-badge>
          </q-btn>
          <q-btn flat round dense icon="account_circle" class="action-btn" />
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="custom-drawer">
      <div class="drawer-header">
        <q-icon name="business_center" size="32px" class="drawer-icon" />
        <div class="drawer-title">CustomerHub</div>
      </div>

      <q-list class="menu-list">
        <q-item-label header class="menu-header"> Main Menu </q-item-label>

        <q-item
          v-for="link in menuLinks"
          :key="link.title"
          clickable
          v-ripple
          class="menu-item"
          active-class="menu-item-active"
        >
          <q-item-section avatar>
            <q-icon :name="link.icon" />
          </q-item-section>

          <q-item-section>
            <q-item-label>{{ link.title }}</q-item-label>
            <q-item-label caption>{{ link.caption }}</q-item-label>
          </q-item-section>
        </q-item>

        <q-separator class="menu-separator" />

        <q-item-label header class="menu-header"> Quick Actions </q-item-label>

        <q-item
          v-for="action in quickActions"
          :key="action.title"
          clickable
          v-ripple
          class="menu-item"
        >
          <q-item-section avatar>
            <q-icon :name="action.icon" />
          </q-item-section>

          <q-item-section>
            <q-item-label>{{ action.title }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'

const menuLinks = [
  {
    title: 'Dashboard',
    caption: 'Overview & Analytics',
    icon: 'dashboard',
  },
  {
    title: 'Customers',
    caption: 'Manage customer database',
    icon: 'groups',
  },
  {
    title: 'Communications',
    caption: 'Messages & interactions',
    icon: 'chat',
  },
  {
    title: 'Tasks',
    caption: 'Follow-ups & reminders',
    icon: 'task_alt',
  },
  {
    title: 'Reports',
    caption: 'Analytics & insights',
    icon: 'analytics',
  },
  {
    title: 'Settings',
    caption: 'Configure your account',
    icon: 'settings',
  },
]

const quickActions = [
  {
    title: 'Add New Customer',
    icon: 'person_add',
  },
  {
    title: 'Send Message',
    icon: 'send',
  },
  {
    title: 'Create Task',
    icon: 'add_task',
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>

<style scoped lang="scss">
.custom-header {
  background: var(--gradient-dark) !important;
  backdrop-filter: blur(10px);
}

.custom-toolbar {
  padding: 0 var(--spacing-lg);
}

.menu-btn {
  color: var(--color-white);

  &:hover {
    background: rgba(220, 38, 38, 0.2);
  }
}

.brand-title {
  display: flex;
  align-items: center;
  gap: var(--spacing-md);
  font-family: var(--font-heading);
  font-weight: 700;
  font-size: var(--text-xl);
}

.brand-icon {
  color: var(--color-red-primary);
}

.brand-text {
  color: var(--color-white);
}

.header-actions {
  display: flex;
  gap: var(--spacing-sm);
}

.action-btn {
  color: var(--color-white);

  &:hover {
    background: rgba(220, 38, 38, 0.2);
  }
}

// Drawer Styles
.custom-drawer {
  background: var(--color-white);
  border-right: 1px solid var(--color-gray-200);
}

.drawer-header {
  display: flex;
  align-items: center;
  gap: var(--spacing-md);
  padding: var(--spacing-xl);
  background: var(--gradient-dark);
  color: var(--color-white);
  border-bottom: 3px solid var(--color-red-primary);
}

.drawer-icon {
  color: var(--color-red-primary);
}

.drawer-title {
  font-family: var(--font-heading);
  font-size: var(--text-xl);
  font-weight: 700;
}

.menu-list {
  padding: var(--spacing-md);
}

.menu-header {
  color: var(--color-gray-500);
  font-size: var(--text-xs);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  padding: var(--spacing-md) var(--spacing-md) var(--spacing-sm);
}

.menu-item {
  border-radius: var(--radius-md);
  margin-bottom: var(--spacing-xs);
  transition: all var(--transition-base) var(--ease-in-out);

  &:hover {
    background: var(--color-gray-100);

    :deep(.q-icon) {
      color: var(--color-red-primary);
    }
  }

  :deep(.q-item__section--avatar) {
    min-width: 40px;

    .q-icon {
      color: var(--color-gray-600);
      transition: color var(--transition-base) var(--ease-in-out);
    }
  }

  :deep(.q-item__label) {
    font-weight: 600;
    color: var(--color-gray-900);
  }

  :deep(.q-item__label--caption) {
    font-size: var(--text-xs);
    color: var(--color-gray-500);
  }
}

.menu-item-active {
  background: linear-gradient(135deg, rgba(220, 38, 38, 0.1), rgba(239, 68, 68, 0.05));
  border-left: 3px solid var(--color-red-primary);

  :deep(.q-icon) {
    color: var(--color-red-primary) !important;
  }

  :deep(.q-item__label) {
    color: var(--color-red-primary);
  }
}

.menu-separator {
  margin: var(--spacing-lg) 0;
  background: var(--color-gray-200);
}

@media (max-width: 768px) {
  .brand-text {
    font-size: var(--text-base);
  }

  .header-actions {
    gap: 0;
  }
}
</style>
