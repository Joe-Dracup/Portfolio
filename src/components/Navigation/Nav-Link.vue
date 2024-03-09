<!-- ToDo: close the nav menu on button click -->

<script setup lang="ts">
let props = defineProps({
  To: String,
  Name: String
})
</script>

<template>
  <div class="link-container">
    <RouterLink class="link" :to="props.To">{{ props.Name }}</RouterLink>
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
