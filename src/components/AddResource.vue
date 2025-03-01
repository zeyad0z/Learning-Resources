<template>
  <base-dialoge
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p>Unfortunately, at least one input value is invalid</p>
      <p>
        Please check all inputs and make sure you enter a few characters into
        each input field.
      </p>
    </template>
    <template #actions>
      <base-btn @click="confirmError">Okay</base-btn>
    </template>
  </base-dialoge>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="title" />
      </div>
      <div class="form-control">
        <label for="desc">Description</label>
        <textarea rows="3" name="desc" id="desc" ref="desc"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="link" />
      </div>
      <div><base-btn type="submit">Add Resource</base-btn></div>
    </form>
  </base-card>
</template>

<script>
export default {
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  inject: ["addResource"],
  methods: {
    submitData() {
      const enterdTitle = this.$refs.title.value;
      const enterdDesc = this.$refs.desc.value;
      const enterdLink = this.$refs.link.value;
      if (
        enterdTitle.trim() === "" ||
        enterdDesc.trim() === "" ||
        enterdLink.trim() === ""
      ) {
        this.inputIsInvalid = true;
        return;
      }
      this.addResource(enterdTitle, enterdDesc, enterdLink);
    },
    confirmError() {
      this.inputIsInvalid = false;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
