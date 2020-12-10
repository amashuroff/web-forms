<template>
  <SignUpForm />
</template>

<script>
import SignUpForm from "./components/SignUpForm";
export default {
  name: "App",
  components: {
    SignUpForm,
  },
};
</script>

<style>
body {
  background-color: grey;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #eee;
  margin-top: 60px;
}
</style>
