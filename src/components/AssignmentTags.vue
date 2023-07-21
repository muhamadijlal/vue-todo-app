<script>
export default {
  props: {
    initialTags: Array,
    currentTag: String,
  },

  computed: {
    tags() {
      return ["all", ...new Set(this.initialTags)];
    },
  },
};
</script>

<template>
  <div class="tags">
    <button
      @click="$emit('update:currentTag', tag)"
      class="badge"
      :class="{ active: tag === currentTag }"
      v-for="tag in tags"
      :key="tag"
    >
      {{ tag }}
    </button>
  </div>
</template>

<style scoped>
.badge {
  margin: 2px;
  padding: 2px 15px;
}

.tags {
  display: flex;
  gap: 2;
  margin: 20px 0;
  flex-wrap: wrap;
}

.active {
  color: #6366f1;
  border: 0.5;
  border-color: #6366f1;
  outline: none;
}
</style>
