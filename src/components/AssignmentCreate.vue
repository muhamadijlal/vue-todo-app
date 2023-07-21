<script>
export default {
  data() {
    return {
      newAssignment: "",
    };
  },
  methods: {
    add() {
      this.$emit("add", this.newAssignment);

      this.clear();
    },

    clear() {
      this.newAssignment = "";
    },
  },
};
</script>

<template>
  <form @submit.prevent="add">
    <div class="form">
      <input
        v-model="newAssignment"
        type="text"
        placeholder="New assignment..."
      />
      <button type="submit">Add</button>
    </div>
  </form>
</template>

<style scoped>
.form {
  display: flex;
  align-items: center;
  gap: 2;
}

button {
  border-radius: 0;
  padding: 8px 15px;
}

input {
  width: 100%;
  height: 35px;
  border-radius: 0;
  border: none;
  outline: none;
  background-color: #6b7280;
}

input::placeholder {
  color: white;
}
</style>
