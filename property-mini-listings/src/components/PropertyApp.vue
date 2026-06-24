<template>
  <section class="property-app">
    <HeaderBar :total="filteredProperties.length" />

    <div class="controls" aria-label="Property filters">
      <label class="field">
        <span>Search</span>
        <input
          v-model="search"
          placeholder="Search by title or location"
          type="search"
        />
      </label>

      <label class="field">
        <span>Sort</span>
        <select v-model="sort">
          <option value="asc">Price: Low -> High</option>
          <option value="desc">Price: High -> Low</option>
        </select>
      </label>
    </div>

    <div v-if="sortedProperties.length" class="grid">
      <PropertyCard
        v-for="p in sortedProperties"
        :key="p.id"
        :property="p"
        @toggle-bookmark="toggleBookmark"
      />
    </div>

    <div v-else class="empty-state">
      <p>No properties match your filters yet.</p>
      <button type="button" @click="resetFilters">Reset filters</button>
    </div>
  </section>
</template>

<script>
import PropertyCard from "./PropertyCard.vue";
import HeaderBar from "./HeaderBar.vue";

export default {
  name: "PropertyApp",
  components: { PropertyCard, HeaderBar },
  data() {
    return {
    search: "",
    sort: "asc",
      properties: [
        {
          id: 1,
          title: "Sea View Loft",
          location: "Sea Point",
          price: 2500,
          type: "Apartment",
          available: true,
          image:
            "https://images.unsplash.com/photo-1494526585095-c41746248156?auto=format&fit=crop&w=1200&q=80",
          bookmarked: false,
        },
        {
          id: 2,
          title: "Garden Cottage",
          location: "Camps Bay",
          price: 4200,
          type: "Cottage",
          available: false,
          image:
            "https://images.unsplash.com/photo-1512917774080-9991f1c4c750?auto=format&fit=crop&w=1200&q=80",
          bookmarked: false,
        },
        {
          id: 3,
          title: "City Studio",
          location: "Cape Town CBD",
          price: 1800,
          type: "Studio",
          available: true,
          image:
            "https://images.unsplash.com/photo-1505693416388-ac5ce068fe85?auto=format&fit=crop&w=1200&q=80",
          bookmarked: false,
        },
        {
          id: 4,
          title: "Mountain Retreat",
          location: "Table Mountain",
          price: 3600,
          type: "House",
          available: true,
          image:
            "https://images.unsplash.com/photo-1502672260266-1c1ef2d93688?auto=format&fit=crop&w=1200&q=80",
          bookmarked: false,
        },
        {
          id: 5,
          title: "Sunny Duplex",
          location: "Clifton",
          price: 3000,
          type: "Duplex",
          available: false,
          image:
            "https://images.unsplash.com/photo-1513694203232-719a280e022f?auto=format&fit=crop&w=1200&q=80",
          bookmarked: false,
        },
      ],
    };
  },
  computed: {
    filteredProperties() {
      const q = this.search.trim().toLowerCase();
      if (!q) return this.properties;
      return this.properties.filter(
        (property) =>
          property.title.toLowerCase().includes(q) ||
          property.location.toLowerCase().includes(q),
      );
    },
    sortedProperties() {
      const properties = [...this.filteredProperties];
      return properties.sort((a, b) =>
        this.sort === "asc" ? a.price - b.price : b.price - a.price,
      );
    },
  },
  methods: {
    toggleBookmark(id) {
      const index = this.properties.findIndex((property) => property.id === id);
      if (index !== -1) {
        this.properties[index].bookmarked = !this.properties[index].bookmarked;
      }
    },
  },
};
</script>

<style scoped>
.property-app {
  display: grid;
  gap: 0.9rem;
}

.controls {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 0.75rem;
}

.field {
  display: grid;
  gap: 0.4rem;
}

.field span {
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--color-muted);
}

.controls input,
.controls select {
  min-height: 2.9rem;
  padding: 0.75rem 0.9rem;
  border: 1px solid var(--color-border);
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.9);
  color: var(--color-heading);
  box-shadow: 0 8px 18px rgba(18, 28, 44, 0.04);
}

.controls input:focus,
.controls select:focus {
  outline: 2px solid rgba(86, 119, 255, 0.28);
  outline-offset: 2px;
}

.grid {
  display: grid;
  gap: 0.9rem;
  grid-template-columns: repeat(1, minmax(0, 1fr));
}

@media (min-width: 640px) {
  .grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (min-width: 1024px) {
  .grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .controls {
    align-items: end;
  }
}

@media (max-width: 860px) {
  .controls {
    grid-template-columns: 1fr;
  }
}
</style>
