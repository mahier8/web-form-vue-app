<template>
  <form>
    <label>Email:</label>
    <input type="email" required v-model="email" />
    <!--  -->
    <label>Password:</label>
    <input type="password" required v-model="password" />
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
      {{ skill }}
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
</style>
