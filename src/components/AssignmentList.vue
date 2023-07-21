<script>
import Assignment from "./Assignment.vue";
import AssignmentTags from "./AssignmentTags.vue";
import Panel from "./Panel.vue";

export default {
  components: { Assignment, AssignmentTags, Panel },
  props: {
    assignments: Array,
    title: String,
    canToggle: { type: Boolean, default: false },
  },
  data() {
    return {
      currentTag: "all",
    };
  },
  computed: {
    filteredAssignments() {
      if (this.currentTag === "all") {
        return this.assignments;
      }

      return this.assignments.filter((a) => a.tag === this.currentTag);
    },
  },
};
</script>

<template>
  <panel v-show="assignments.length" class="list">
    <div class="header">
      <h2>
        {{ title }}
        <span> ({{ assignments.length }}) </span>
      </h2>

      <button class="logo" v-show="canToggle" @click="$emit('toggle')">
        &times;
      </button>
    </div>

    <assignment-tags
      v-model:currentTag="currentTag"
      :initial-tags="assignments.map((a) => a.tag)"
    />

    <ul>
      <assignment
        v-for="assignment in filteredAssignments"
        :assignment="assignment"
        :key="assignment.id"
      />
    </ul>

    <slot />

    <template #footer>
      <div>My footer goes here</div>
    </template>
  </panel>
</template>

<style scoped>
h2 {
  margin: 0;
}
.header {
  display: flex;
  justify-content: space-between;
  place-items: start;
}

.list {
  width: 15rem;
  background-color: #374151;
  border: 1px solid #4b5563;
  padding: 1rem;
  border-radius: 0.5rem;
}

.logo {
  border: 0;
  background-color: none;
  outline: none;
  padding: 0;
  height: 0;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
</style>
