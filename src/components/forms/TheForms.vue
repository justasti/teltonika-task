<template>
  <div class="secondary-nav">
    <BaseButton @click="setSelectedTab('NewUserForm')" :mode="newUserButtonMode"
      >New user</BaseButton
    >
    <BaseButton
      @click="setSelectedTab('NewCategoryForm')"
      :mode="newCategoryButtonMode"
      >New category</BaseButton
    ><BaseButton
      @click="setSelectedTab('NewSubcategoryForm')"
      :mode="newSubcatButtonMode"
      >New sub-category</BaseButton
    ><BaseButton
      @click="setSelectedTab('NewSubSubCategoryForm')"
      :mode="newSubsubcatButtonMode"
      >New sub-sub-category</BaseButton
    >
  </div>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import NewUserForm from "./NewUserForm.vue";
import NewCategoryForm from "./NewCategoryForm.vue";
import NewSubcategoryForm from "./NewSubcategoryForm.vue";
import NewSubSubCategoryForm from "./NewSubSubCategoryForm.vue";
export default {
  components: {
    NewUserForm,
    NewCategoryForm,
    NewSubcategoryForm,
    NewSubSubCategoryForm,
  },
  data() {
    return {
      selectedTab: "NewUserForm",
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
  computed: {
    newUserButtonMode() {
      return this.selectedTab === "NewUserForm" ? null : "flat";
    },
    newCategoryButtonMode() {
      return this.selectedTab === "NewCategoryForm" ? null : "flat";
    },
    newSubcatButtonMode() {
      return this.selectedTab === "NewSubcategoryForm" ? null : "flat";
    },
    newSubsubcatButtonMode() {
      return this.selectedTab === "NewSubSubCategoryForm" ? null : "flat";
    },
  },
};
</script>

<style>
form {
  padding: 2rem;
}
input {
  border: none;
  border-bottom: 3px #333 solid;
  border-radius: 10px 10px 10px 0;
  font: inherit;
  display: block;
  margin-bottom: 1rem;
  outline: none;
  padding: 0.25rem;
  width: 40vw;
}
input:focus {
  background-color: #f4f4f4;
}
input[type="radio"] {
  display: inline;
  width: auto;
  margin-right: 0.25rem;
  margin-bottom: 0;
}
select {
  border-radius: 5px;
  font-family: inherit;
  padding: 0.25rem;
  display: block;
  margin-block: 0.75rem;
  min-width: 10rem;
}
.wide {
  width: 100%;
}
.secondary-nav {
  margin-bottom: 2rem;
  display: flex;
  justify-content: center;
}
</style>
