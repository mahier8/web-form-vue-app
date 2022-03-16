<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email" />
    <!--  -->
    <label>Password:</label>
    <input type="password" required v-model="password" />
    <div v-if="passwordError" class="error">{{ passwordError }}</div>
    <!--  -->
    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>
    <!--  -->
    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>
    <!--  -->
    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Accept terms and conditions</label>
    </div>
    <!--  -->
    <!-- we dont need the below in our form later 1. -->
    <!-- <div>
      <input type="checkbox" value="mahier" v-model="names" />
      <label>Mahier</label>
    </div>
    <div>
      <input type="checkbox" value="angel" v-model="names" />
      <label>Angel</label>
    </div>
    <div>
      <input type="checkbox" value="friend" v-model="names" />
      <label>Friend</label>
    </div> -->
    <div class="submit">
      <button>Create an Account</button>
    </div>
  </form>
  <!--  -->
  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
  <!-- we dont need the below in our form later 2. -->
  <!-- <p>Names: {{ names }}</p> -->
</template>

<script>
export default {
  data() {
    // we can track what the user inputs/selects
    return {
      email: "mahier",
      password: "",
      role: "designer",
      // we use a boolean, as there are only two choices here
      terms: false,
      // when we use multiple input fields, that are of type checkbox
      // we dont need the below in our form later 3.
      //   names: [],
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      // if , is pressed and the tempskill has a value
      if (e.key === "," && this.tempSkill) {
        // will check if the skills array doesnt already have the tempskill
        // then will add to the array if it doesnt have it
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        // to empty the input
        this.tempSkill = "";
      }
    },
    deleteSkill(skill) {
      // we use the filter method on the array
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    handleSubmit() {
      // validate password
      // terniary operator
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Password must be at least 6 characters long";
      // if there is no error
      if (!this.passwordError) {
        // here we would make request to database to save user
        console.log("email: ", this.email);
        console.log("password: ", this.password);
        console.log("role: ", this.role);
        console.log("skills: ", this.skills);
        console.log("terms accepted: ", this.terms);
      }
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
.submit {
  text-align: center;
}
.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>
