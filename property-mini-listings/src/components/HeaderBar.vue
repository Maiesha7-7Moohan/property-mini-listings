<template>
  <header class="property-header">
    <div>
      <div class="brand">Homes & Beyond</div>
      <p class="subtle">A small set of Cape Town properties.</p>
    </div>

    <div class="count">
      {{ total }} properties
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderBar",
  props: {
    total: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style scoped>
.property-header {
  display: flex;
  flex-wrap: wrap;
  align-items: end;
  justify-content: space-between;
  gap: 0.75rem;
  padding: 0.35rem 0 0.5rem;
  border: 1px solid var(--color-border);
  border-width: 0 0 1px;
  border-radius: 0;
  background: transparent;
  box-shadow: none;
  backdrop-filter: none;
}

.brand {
  font-family: var(--font-display);
  font-size: clamp(1.5rem, 2vw, 2rem);
  font-weight: 700;
  color: var(--color-heading);
}

.subtle {
  margin: 0.25rem 0 0;
  color: var(--color-muted);
  font-size: 0.95rem;
}

.count {
  color: var(--color-muted);
  font-size: 0.95rem;
  font-weight: 700;
}
</style>
