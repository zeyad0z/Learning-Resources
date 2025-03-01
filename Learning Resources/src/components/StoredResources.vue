<template>
  <ul>
    <resources-item
      v-for="item in learningItems"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :desc="item.desc"
      :link="item.link"
    ></resources-item>
  </ul>
</template>

<script>
import ResourcesItem from "./ResourcesItem.vue";
export default {
  components: { ResourcesItem },
  inject: ["learningItems"],
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
