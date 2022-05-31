<template>
  <section v-for="category in filteredCategories" :key="category.name">
    <div :key="category.name">
      <h2 v-if="filteredName" class="category-title">{{ category.name }}</h2>
      <SubCategoriesList
        v-bind="{ selectedValue, category }"
      ></SubCategoriesList>
    </div>
  </section>
</template>

<script>
import SubCategoriesList from "./SubCategoriesList.vue";
import { HOMEPAGE } from "./constants/constants";
export default {
  components: { SubCategoriesList },
  inject: ["categories"],
  props: { selectedValue: { type: String, required: true } },
  computed: {
    filteredName() {
      if (this.selectedValue === HOMEPAGE) {
        return true;
      }
      return this.categories.find((item) => item.name === this.selectedValue);
    },
    filteredCategories() {
      if (this.categories.find((item) => item.name === this.selectedValue)) {
        return this.categories.filter(
          (category) => category.name === this.selectedValue
        );
      }
      return this.categories;
    },
  },
};
</script>

<style scoped>
.category-title {
  text-align: center;
  padding: 0.55rem 0;
}
div {
  border: 1px #333 solid;
  border-radius: 10px;
  margin-bottom: 1rem;
}
</style>
