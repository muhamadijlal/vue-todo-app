<script>
import AssignmentList from "./AssignmentList.vue";
import AssignmentCreate from "./AssignmentCreate.vue";

export default {
  components: { AssignmentList, AssignmentCreate },
  data() {
    return {
      assignments: [],
      showCompleted: true,
    };
  },
  created() {
    fetch("http://localhost:3000/assignments")
      .then((response) => response.json())
      .then((assignments) => (this.assignments = assignments));
  },
  computed: {
    filters() {
      return {
        inProgress: this.assignments.filter((a) => !a.complete),
        completed: this.assignments.filter((a) => a.complete),
      };
    },
  },
  methods: {
    add(name) {
      this.assignments.push({
        id: this.assignments.length + 1,
        name: name,
        complete: false,
      });
    },
  },
};
</script>

<template>
  <section class="wrap">
    <assignment-list :assignments="filters.inProgress" title="In Progress">
      <assignment-create @add="add" />
    </assignment-list>
    <assignment-list
      v-show="showCompleted"
      :assignments="filters.completed"
      can-toggle
      title="Completed"
      @toggle="showCompleted = !showCompleted"
    />
  </section>
</template>

<style scoped>
.wrap {
  display: flex;
  gap: 2rem;
}
</style>
