<template>
  <template v-for="category in categories" :key="category.name">
    <template v-for="subcategory in category.subcats" :key="subcategory.name">
      <div>
        <h2 v-if="filteredName" class="subcategory-title">
          {{ subcategory.name }}
        </h2>
        <SubSubCategoriesList
          v-bind="{ selectedValue, subcategory }"
        ></SubSubCategoriesList>
      </div>
    </template>
  </template>
</template>

<script>
import SubSubCategoriesList from "./SubSubCategoriesList.vue";
import { HOMEPAGE } from "./constants/constants";
export default {
  props: {
    selectedValue: { type: String, required: true },
    category: { type: Object, required: true },
  },
  inject: ["categories"],
  components: { SubSubCategoriesList },
  computed: {
    filteredName() {
      if (this.selectedValue === HOMEPAGE) {
        return true;
      }
      return this.category.subcats.find(
        (item) => item.name === this.selectedValue
      );
    },
  },
};
</script>

<style scoped>
.subcategory-title {
  text-align: center;
  padding: 0.55rem 0;
  font-size: 1.25rem;
}
div {
  border: 1px #333 solid;
  border-radius: 10px;
  margin-bottom: 1rem;
  padding: 1rem;
}
</style>
