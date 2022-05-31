<template>
  <template v-for="category in categories" :key="category.name">
    <template v-for="subcategory in category.subcats" :key="subcategory.name">
      <template v-for="subsub in subcategory.subsubcats" :key="subsub.name">
        <div class="subsubcategories">
          <h2>{{ subsub.name }}</h2>
          <div class="users-content">
            <template v-for="user in users" :key="user.email">
              <div class="user-card" v-if="filteredUsers">
                <p v-for="value in user" :key="value">{{ value }}</p>
              </div>
            </template>
          </div>
        </div>
      </template>
    </template>
  </template>
</template>
<script>
export default {
  inject: ["users", "categories"],
  props: { selectedValue: { type: String, required: true } },
  computed: {
    filteredUsers() {
      return this.users.find((user) =>
        user.category.includes(this.selectedValue)
      );
    },
  },
};
</script>

<style scoped>
h2 {
  text-align: center;
  padding: 0;
  font-size: 1rem;
}
p {
  display: block;
  text-align: center;
}
.user-card {
  border: 1px black solid;
  width: 180px;
  padding: 0.75rem;
  border-radius: 10px;
  margin: 0.75rem;
}
.users-content {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  border: 1px black solid;
  border-radius: 10px;
}
.subsubcategories {
  border: 1px solid black;
  border-radius: 10px;
  padding: 1rem;
  margin-bottom: 1.5rem;
}
</style>
