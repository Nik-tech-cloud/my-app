<template>
  <div class="title-container">
    <h1>{{ text }}</h1>
  </div>
</template>
<script>

export default {
  name: "Title",
  props: ["text"]
};
</script>
<style scoped>
.title-container {
    display: flex;
    justify-content: center;
}
</style>