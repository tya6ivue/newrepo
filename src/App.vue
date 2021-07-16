<template>
  <div id="app">
    <InputForm />
    <Assignmnt />
    <Assignment />
  </div>
</template>

<script>
import Assignment from "./components/Assignment.vue";
import InputForm from "./components/InputForm.vue";
import Assignmnt from "./components/Assignmnt.vue";
export default {
  name: "App",
  components: {
    InputForm,
    Assignmnt,
    Assignment,
  },
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
</style>
