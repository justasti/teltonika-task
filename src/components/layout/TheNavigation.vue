<template>
  <nav>
    <ul @click="selectNavItem">
      <li title="Home">{{ $options.HOMEPAGE }}</li>
      <li title="New data">{{ $options.NEW_DATA }}</li>
      <template v-for="category in categories" :key="category.name">
        <li :title="category.name">
          {{ category.name }}
        </li>
        <ul>
          <template v-for="subcat in category.subcats" :key="subcat.name">
            <li :title="subcat.name">
              {{ subcat.name }}
            </li>
            <ul>
              <template
                v-for="subsubcat in subcat.subsubcats"
                :key="subsubcat.name"
              >
                <li :title="subsubcat.name">{{ subsubcat.name }}</li>
              </template>
            </ul>
          </template>
        </ul>
      </template>
    </ul>
  </nav>
</template>

<script>
import { NEW_DATA, HOMEPAGE } from "../constants/constants";
export default {
  NEW_DATA,
  HOMEPAGE,
  inject: ["categories"],
  emits: ["nav-selection"],
  methods: {
    selectNavItem($event) {
      const { value } = $event.target.attributes.title;
      this.$emit("nav-selection", value);
    },
  },
};
</script>

<style scoped>
nav {
  margin-block: 2rem;
  padding-inline: 1rem;
}
li {
  list-style: none;
  padding-block: 0.25rem;
  cursor: pointer;
}
li:hover {
  font-weight: bold;
}
ul > ul {
  padding-left: 0.5rem;
}
</style>
