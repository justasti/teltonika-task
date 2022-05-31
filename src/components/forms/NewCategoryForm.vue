<template>
  <h2>Create a new category</h2>
  <form @submit.prevent="addNewCategory">
    <div>
      <input
        type="text"
        name="category"
        id="category"
        placeholder="Enter the name for a new category"
        v-model="category"
      />
    </div>
    <BaseButton>Submit</BaseButton>
  </form>
</template>

<script>
export default {
  inject: ["categories"],
  methods: {
    addNewCategory() {
      this.categories.push({ name: this.category, subcats: [] });
      this.category = "";
    },
  },
  data() {
    return {
      category: "",
    };
  },
};
</script>
