<template>
  <base-card>
    <base-btn @click="toggleSelect('stored-resources')" :mode="storedBtnMode"
      >Stored Resources</base-btn
    >
    <base-btn @click="toggleSelect('add-resource')" :mode="addBtnMode"
      >Add Resource</base-btn
    >
  </base-card>
  <keep-alive>
    <component :is="selected"></component>
  </keep-alive>
</template>

<script>
import AddResource from "./AddResource.vue";
import StoredResources from "./StoredResources.vue";

export default {
  components: { StoredResources, AddResource },
  data() {
    return {
      selected: "stored-resources",
      learningItems: [
        {
          id: "official-guide",
          title: "Official Guide",
          desc: "The official Vue.js documentation",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          desc: "Learn to google...",
          link: "https://google.org",
        },
      ],
    };
  },
  methods: {
    toggleSelect(cmp) {
      this.selected = cmp;
    },
    addResource(title, desc, link) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        desc: desc,
        link: link,
      };
      this.learningItems.unshift(newResource);
      this.selected = "stored-resources";
    },
    removeResource(itemId) {
      const itemidx = this.learningItems.findIndex(
        (itme) => itemId.Id === itemId
      );
      this.learningItems.splice(itemidx, 1);
    },
  },
  provide() {
    return {
      learningItems: this.learningItems,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },
  computed: {
    storedBtnMode() {
      return this.selected === "stored-resources" ? null : "flat";
    },
    addBtnMode() {
      return this.selected === "add-resource" ? null : "flat";
    },
  },
};
</script>
