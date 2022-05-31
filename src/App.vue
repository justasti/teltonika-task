<template>
  <TheHeader />
  <div class="main-content">
    <TheNavigation @nav-selection="selectTab($event)" />
    <BaseCard>
      <component :is="selectedTab" v-bind="{ selectedValue }"></component>
    </BaseCard>
  </div>
  <TheFooter></TheFooter>
</template>
<script>
import TheHeader from "./components/layout/TheHeader.vue";
import TheFooter from "./components/layout/TheFooter.vue";
import TheNavigation from "./components/layout/TheNavigation.vue";
import TheForms from "./components/forms/TheForms.vue";
import CategoriesList from "./components/CategoriesList.vue";
export default {
  components: { TheHeader, TheFooter, TheNavigation, TheForms, CategoriesList },
  data() {
    return {
      users: [
        {
          password: "123asd",
          name: "Justas",
          lastName: "Tir",
          email: "jus@ta.s",
          age: 22,
          phone: "+37061234567",
          gender: "male",
          category: "cat1-subcat1-subsubcat2",
        },
      ],
      categories: [
        {
          name: "cat1",
          subcats: [
            {
              name: "cat1-subcat1",
              subsubcats: [
                { name: "cat1-subcat1-subsubcat1" },
                { name: "cat1-subcat1-subsubcat2" },
              ],
            },
          ],
        },
        {
          name: "cat2",
          subcats: [
            {
              name: "cat2-subcat1",
              subsubcats: [
                { name: "cat2-subcat1-subsubcat1" },
                { name: "cat2-subcat1-subsubcat2" },
              ],
            },
          ],
        },
      ],
      selectedTab: "CategoriesList",
      selectedValue: "cat1",
    };
  },

  provide() {
    return {
      users: this.users,
      categories: this.categories,
    };
  },
  methods: {
    selectTab(value) {
      if (value === "New data") {
        this.selectedTab = "TheForms";
      } else {
        this.selectedTab = "CategoriesList";
        this.selectedValue = value;
      }
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700&display=swap");
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  color: #333;
  background-color: #eee;
  font-family: "Lato", sans-serif;
  height: 100vh;
  max-width: 1000px;
  margin-inline: auto;
}
.main-content {
  display: grid;
  grid-template-columns: 3fr 7fr;
  padding: 1rem;
  background-color: #fff;
}
h2 {
  padding-left: 2rem;
}
.fail {
  color: red;
  padding-left: 2rem;
  margin-top: -1.5rem;
}
.success {
  color: green;
  padding-left: 2rem;
  margin-top: -1.5rem;
}
.categories-data {
  margin-block: 2rem;
}
</style>
