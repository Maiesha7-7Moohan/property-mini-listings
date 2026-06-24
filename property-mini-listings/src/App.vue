<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="shell">
    <header class="shell-header">
      <div class="brand">
        <p class="eyebrow">Mini Listings</p>
        <h1>Property shortlist</h1>
        <p class="lede">
          Search, sort, and bookmark a compact set of Cape Town rentals.
        </p>
      </div>

      <nav class="shell-nav" aria-label="Primary">
        <RouterLink to="/">Homes</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </header>

    <RouterView />
  </div>
</template>

<style scoped>
.shell {
  width: min(1180px, calc(100% - 2rem));
  margin: 0 auto;
  padding: 2rem 0 3rem;
}

.shell-header {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 1.5rem;
  align-items: end;
  margin-bottom: 1.5rem;
}

.brand {
  max-width: 42rem;
}

.eyebrow {
  margin: 0 0 0.5rem;
  text-transform: uppercase;
  letter-spacing: 0.24em;
  font-size: 0.72rem;
  font-weight: 700;
  color: var(--color-accent);
}

h1 {
  margin: 0;
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 4vw, 3.9rem);
  line-height: 0.98;
  color: var(--color-heading);
}

.lede {
  margin: 0.9rem 0 0;
  max-width: 34rem;
  font-size: 1rem;
  color: var(--color-muted);
}

.shell-nav {
  display: inline-flex;
  gap: 0.5rem;
  padding: 0.35rem;
  border: 1px solid var(--color-border);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.6);
  backdrop-filter: blur(14px);
}

.shell-nav a {
  display: inline-flex;
  align-items: center;
  min-height: 2.5rem;
  padding: 0 1rem;
  border-radius: 999px;
  color: var(--color-muted);
  text-decoration: none;
  transition:
    color 0.2s ease,
    background-color 0.2s ease,
    transform 0.2s ease;
}

.shell-nav a:hover {
  background: rgba(18, 28, 44, 0.06);
  transform: translateY(-1px);
}

.shell-nav a.router-link-exact-active {
  color: var(--color-heading);
  background: rgba(18, 28, 44, 0.1);
}

@media (max-width: 720px) {
  .shell {
    width: min(100% - 1rem, 1180px);
    padding-top: 1rem;
  }

  .shell-header {
    align-items: start;
  }
}
</style>
