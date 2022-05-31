<template>
  <h2>Create a new sub-sub-category</h2>
  <form @submit.prevent="addNewSubsubcat(chosenSubcat, newSubsubcat)">
    <div>
      <input
        type="text"
        name="newSubcat"
        id="newSubcat"
        v-model="newSubsubcat"
        placeholder="Enter the name for a new sub-category"
      />
      <label for="available-categories"
        >Please choose a sub-category for the new sub-sub-category:
      </label>
      <select
        name="available-categories"
        id="available-categories"
        v-model="chosenSubcat"
      >
        <template v-for="category in categories" :key="category.name">
          <option
            :value="subcategory.name"
            v-for="subcategory in category.subcats"
            :key="subcategory.name"
          >
            {{ subcategory.name }}
          </option>
        </template>
      </select>
    </div>
    <BaseButton>Submit</BaseButton>
  </form>
</template>

<script>
export default {
  inject: ["categories"],
  methods: {
    addNewSubsubcat(subcat, subsubcat) {
      let subcatToFill;
      for (let i = 0; i < this.categories.length; i += 1) {
        for (let j = 0; j < this.categories[i].subcats.length; j += 1) {
          if (this.categories[i].subcats[j].name === subcat) {
            subcatToFill = this.categories[i].subcats[j];
          }
        }
      }
      subcatToFill.subsubcats.push({ name: subsubcat });
    },
  },
  data() {
    return {
      chosenSubcat: "",
      newSubsubcat: "",
    };
  },
};
</script>
<style scoped>
label {
  margin-block: 0.5rem;
}
</style>
