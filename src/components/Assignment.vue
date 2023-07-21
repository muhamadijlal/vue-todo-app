<script>
export default {
  props: {
    assignment: Object,
  },
};
</script>

<template>
  <li>
    <label>
      {{ assignment.name }}

      <input type="checkbox" v-model="assignment.complete" />
    </label>
  </li>
</template>

<style scoped>
li {
  border: 1px solid gray;
  padding: 10px;
}
</style>
