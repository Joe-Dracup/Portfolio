<script setup lang="ts">
import router from '@/router'

const props = defineProps({
  To: { type: String, required: true },
  Name: String
})

const emit = defineEmits(['navigating'])

function handleClick() {
  emit('navigating')
  router.push({ path: props.To })
}
</script>

<template>
  <div class="link-container">
    <a class="link" @click="handleClick()">
      {{ props.Name }}
    </a>
  </div>
</template>

<style scoped>
@import '../../assets/variables.css';

.link-container {
  background-color: var(--color-background-soft);
  padding: 0.6rem;
}

@media screen and (min-width: 1024px) {
  .link-container {
    padding: 0.3rem;
  }
}

.link-container .link {
  color: var(--color-text);
  padding: 0.66rem;
  display: flex;
}
</style>
