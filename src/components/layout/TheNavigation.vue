<template>
  <nav>
    <ul @click="selectNavItem">
      <li>Home</li>
      <li>New data</li>
      <template v-for="category in categories" :key="category.name">
        <li>
          {{ category.name }}
        </li>
        <ul>
          <template v-for="subcat in category.subcats" :key="subcat.name">
            <li>
              {{ subcat.name }}
            </li>
            <ul>
              <template
                v-for="subsubcat in subcat.subsubcats"
                :key="subsubcat.name"
              >
                <li>{{ subsubcat.name }}</li>
              </template>
            </ul>
          </template>
        </ul>
      </template>
    </ul>
  </nav>
</template>

<script>
export default {
  inject: ["categories"],
  emits: ["nav-selection"],
  methods: {
    selectNavItem($event) {
      this.$emit("nav-selection", $event.target.innerText);
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
