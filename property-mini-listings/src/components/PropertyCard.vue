<template>
  <article class="card">
    <div class="image" :style="imageStyle">
      <button class="bookmark" type="button" :aria-label="bookmarkLabel" @click="$emit('toggle-bookmark', property.id)">
        {{ property.bookmarked ? "Saved" : "Save" }}
      </button>
    </div>

    <div class="content">
      <h3 class="title">{{ property.title }}</h3>
      <p class="meta">{{ property.location }} | {{ property.type }}</p>
      <p class="price">R {{ property.price.toLocaleString() }}</p>
    </div>
  </article>
</template>

<script>
export default {
  name: "PropertyCard",
  emits: ["toggle-bookmark"],
  props: {
    property: {
      type: Object,
      required: true,
    },
  },
  computed: {
    imageStyle() {
      const url = this.property.image || "";
      return {
        backgroundImage: url ? `url(${url})` : "linear-gradient(135deg, #d9e0ea, #f7f3ea)",
      };
    },
    bookmarkLabel() {
      return this.property.bookmarked ? "Remove bookmark" : "Add bookmark";
    },
  },
};
</script>

<style scoped>
.card {
  overflow: hidden;
  display: flex;
  flex-direction: column;
  border: 1px solid var(--color-border);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.88);
}

.image {
  position: relative;
  height: 180px;
  background-size: cover;
  background-position: center;
}

.bookmark {
  position: absolute;
  right: 0.8rem;
  top: 0.8rem;
  z-index: 1;
  min-width: 4rem;
  min-height: 2.3rem;
  padding: 0 0.8rem;
  border: none;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.92);
  color: #111827;
  font-size: 0.78rem;
  font-weight: 700;
  cursor: pointer;
}

.content {
  display: grid;
  gap: 0.25rem;
  padding: 0.9rem 1rem 1rem;
}

.title {
  margin: 0;
  font-size: 1rem;
  line-height: 1.25;
  color: var(--color-heading);
}

.price {
  margin: 0.3rem 0 0;
  font-weight: 700;
  color: var(--color-heading);
}

.meta {
  margin: 0;
  color: var(--color-muted);
  font-size: 0.88rem;
}
</style>
