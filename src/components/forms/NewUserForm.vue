<template>
  <div>
    <h2>Add new user</h2>
    <form @submit.prevent="addNewUser">
      <input
        type="password"
        placeholder="Please enter a password"
        id="password"
        v-model="password"
      />
      <input
        type="text"
        placeholder="Please enter a name"
        id="name"
        v-model="name"
      />
      <input
        type="text"
        placeholder="Please enter a last name"
        id="lastName"
        v-model="lastName"
      />
      <input
        type="email"
        placeholder="Please enter an email"
        id="email"
        v-model="email"
      />
      <input
        type="number"
        placeholder="Please enter the age"
        id="age"
        v-model="age"
      />
      <input
        type="text"
        placeholder="Please enter a phone number"
        id="phone"
        v-model="phone"
      />
      <div class="radio-inputs">
        <input
          type="radio"
          id="gender-male"
          name="gender"
          value="male"
          v-model="gender"
        />
        <label for="gender-male">Male</label>
      </div>
      <div class="radio-inputs">
        <input
          type="radio"
          id="gender-female"
          name="gender"
          value="female"
          v-model="gender"
        />
        <label for="gender-female">Female</label>
      </div>
      <select id="category" name="category" v-model="category">
        <option value="" selected disabled>Please choose a category</option>
        <template v-for="category in categories" :key="category.name">
          <template v-for="subcat in category.subcats" :key="subcat.name">
            <template
              v-for="subsubcat in subcat.subsubcats"
              :key="subsubcat.name"
            >
              <option :value="subsubcat.name">{{ subsubcat.name }}</option>
            </template>
          </template>
        </template>
      </select>
      <BaseButton>Submit</BaseButton>
    </form>
    <p class="fail" v-if="isInputValid === 'false'">
      At least one field is empty! Please check the inputs and try again.
    </p>
    <p class="success" v-else-if="isInputValid === 'true'">
      User successfully added.
    </p>
  </div>
</template>

<script>
export default {
  inject: ["users", "categories"],
  data() {
    return {
      password: "",
      name: "",
      lastName: "",
      email: "",
      age: null,
      phone: "",
      gender: "",
      category: "",
      isInputValid: "pending",
    };
  },
  methods: {
    addNewUser() {
      const newUser = {
        password: this.password,
        name: this.name,
        lastName: this.lastName,
        email: this.email,
        age: this.age,
        phone: this.phone,
        gender: this.gender,
        category: this.category,
      };
      if (
        this.password === "" ||
        this.name === "" ||
        this.lastName === "" ||
        this.email === "" ||
        this.age === "" ||
        this.phone === "" ||
        this.gender === "" ||
        this.category === ""
      ) {
        this.isInputValid = "false";
      } else {
        this.users.push(newUser);
        this.isInputValid = "true";
      }
    },
  },
};
</script>

<style scoped>
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
h2 {
  padding-left: 2rem;
}
.radio-inputs {
  display: inline;
}
.radio-inputs + .radio-inputs {
  padding-left: 1rem;
}
</style>
