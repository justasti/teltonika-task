<template>
  <h2>Create a new sub-category</h2>
  <form @submit.prevent="addNewSubcat(chosenCategory, newSubcat)">
    <div>
      <input
        type="text"
        name="newSubcat"
        id="newSubcat"
        v-model="newSubcat"
        placeholder="Enter the name for a new sub-category"
      />
      <label for="available-categories"
        >Please choose a category for the new sub-category:
      </label>
      <select
        name="available-categories"
        id="available-categories"
        v-model="chosenCategory"
      >
        <option
          :value="category.name"
          v-for="category in categories"
          :key="category.name"
        >
          {{ category.name }}
        </option>
      </select>
    </div>
    <BaseButton>Submit</BaseButton>
  </form>
</template>

<script>
export default {
  inject: ["categories"],
  methods: {
    addNewSubcat(cat, subcat) {
      const catToFill = this.categories.find(
        (category) => category.name === cat
      );
      catToFill.subcats.push({ name: subcat, subsubcats: [] });
    },
  },
  data() {
    return {
      chosenCategory: "",
      newSubcat: "",
    };
  },
};
</script>
<style scoped>
label {
  margin-block: 0.5rem;
}
</style>
