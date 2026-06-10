<script setup>
import { useData } from 'vitepress'
import { computed } from 'vue'

const { frontmatter } = useData()

// Create a computed property to safely access features
const features = computed(() => {
  return frontmatter.value?.features || []
})
</script>

<template>
  <div v-if="features.length" class="features">
    <div v-for="f in features" :key="f.title" class="feature">
      <div class="icon">{{ f.icon }}</div>
      <h3>{{ f.title }}</h3>
      <p>{{ f.details }}</p>
    </div>
  </div>
</template>

<style scoped>
.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin: 2rem 0;
  padding: 2rem 0;
}

.feature {
  text-align: center;
  padding: 1.5rem;
  border-radius: 8px;
  transition: all 0.3s ease;
  border: 1px solid transparent;
}

.feature:hover {
  border-color: var(--vp-c-brand-1);
  background-color: var(--vp-c-brand-soft);
  transform: translateY(-4px);
}

.icon {
  font-size: 3rem;
  margin-bottom: 1rem;
  display: block;
}

.feature h3 {
  margin: 0 0 0.5rem 0;
  font-size: 1rem;
  font-weight: 600;
  color: var(--vp-c-text-1);
}

.feature p {
  margin: 0;
  font-size: 0.875rem;
  color: var(--vp-c-text-2);
  line-height: 1.5;
}

@media (max-width: 640px) {
  .features {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    margin: 1.5rem 0;
    padding: 1.5rem 0;
  }

  .feature {
    padding: 1rem;
  }

  .icon {
    font-size: 2.5rem;
  }
}
</style>
