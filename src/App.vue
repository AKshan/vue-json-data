<template>
  <PersonData />
</template>

<script>
import PersonDataVue from './components/PersonData.vue';
export default {
  name: "App",
  components: {
    PersonData: PersonDataVue,
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
body{
      background: #fff;
}
</style>
