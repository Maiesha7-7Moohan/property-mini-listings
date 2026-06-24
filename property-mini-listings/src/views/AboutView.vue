<template>
  <main class="about">
    <section class="panel">
      <p class="eyebrow">About</p>
      <h1>Built as a compact property browsing experience.</h1>
      <p>
        This mini app demonstrates search, sorting, availability filtering, and bookmark
        toggles over a small curated property set.
      </p>
    </section>
  </main>
</template>

<style scoped>
.about {
  padding: 0.75rem 0 0;
}

.panel {
  max-width: 42rem;
  padding: 1.5rem;
  border: 1px solid var(--color-border);
  border-radius: 28px;
  background: rgba(255, 255, 255, 0.72);
  box-shadow: 0 20px 50px rgba(18, 28, 44, 0.08);
}

.eyebrow {
  margin: 0 0 0.5rem;
  text-transform: uppercase;
  letter-spacing: 0.18em;
  font-size: 0.72rem;
  font-weight: 700;
  color: var(--color-accent);
}

h1 {
  margin: 0;
  font-family: var(--font-display);
  font-size: clamp(1.8rem, 3vw, 2.8rem);
  line-height: 1.05;
  color: var(--color-heading);
}

p {
  margin: 0.95rem 0 0;
  color: var(--color-muted);
  font-size: 1rem;
}
</style>
