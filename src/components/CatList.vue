<template>
  <ul>
    <li v-bind:key="cat" v-for="cat in cats">{{ cat }}</li>
  </ul>
</template>

<script>
export default {
  name: "CatList",
  props: ["cats"],
};
</script>

<style scoped></style>
