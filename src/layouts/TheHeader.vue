<template>
  <header>
    <h1>To-do list</h1>
  </header>
</template>

<script>
export default {
  props: ["title"],
};
</script>

<style scoped>
header {
  max-width: 1200px;

  width: 100%;
  height: 5rem;
  background-color: #0e71bc;
  display: flex;
  justify-content: center;
  align-items: center;
}

header h1 {
  color: white;
  margin: 0;
}
</style>
