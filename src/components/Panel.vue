<script>
export default {
  props: {
    theme: { type: String, default: "dark" },
  },
};
</script>

<template>
  <div
    :class="{
      card: true,
      'card-light': theme == 'light',
      'card-dark': theme == 'dark',
    }"
  >
    <h2 v-if="$slots.heading">
      <slot name="heading" />
    </h2>

    <slot />

    <footer v-if="$slots.footer">
      <slot name="footer" />
    </footer>
  </div>
</template>

<style scoped>
.card {
  padding: 1rem;
  border-radius: 0.5rem;
  margin-top: 2rem;
}

.card-dark {
  background-color: #374151;
  border: 1px solid #4b5563;
  color: white;
}

.card-light {
  background-color: white;
  border: 1px solid black;
  color: black;
}

h2 {
  margin: 0 0 0 10px;
}

footer {
  border-top: 1px solid gray;
  font-size: 12px;
  margin-top: 1rem;
  padding-top: 1rem;
}
</style>
