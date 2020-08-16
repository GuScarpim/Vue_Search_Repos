<template>
  <div id="app">
    <Input v-model="name" />
    <load-data :userName.sync="name"/>
  </div>
</template>

<script>
import LoadData from './components/LoadData'
import Input from "./components/Input";

export default {
  name: "root-container",
  data: () => ({
    name: ''
  }),
  components: {
    Input,
    LoadData,
  }
};
</script>

<style>
body {
  background-color: #323650;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin: 0px;
  height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  -webkit-animation: fadeIn 2s ease-in-out;
  -moz-animation: fadeIn 2s ease-in-out;
  -o-animation: fadeIn 2s ease-in-out;
  animation: fadeIn 2s ease-in-out;
}

  @-webkit-keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; } 
  }
  @-moz-keyframes fadeIn {
  0% { opacity: 0;}
  100% { opacity: 1; }
  }
  @-o-keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
  }
  @keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
  }
</style>