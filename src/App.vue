<template>
  <!-- if we start with placing the component within the template
, we should get the autocomplete, then in the script it should 
import on its own  -->
  <!-- for imports 1. -->
  <SignupForm />
</template>

<script>
// for imports 2.
import SignupForm from "./components/SignupForm.vue";
export default {
  name: "App",
  // for imports 3.
  components: { SignupForm },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background: #eee;
}
</style>
