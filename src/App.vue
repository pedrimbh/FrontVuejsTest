<template>
  <div id="app">
    <ul v-for="item in caminhos" :key="item">
      <li>{{ item.name }} ({{item.size}}kb)</li>
      <li v-for="itens in item.folders" :key="itens">{{itens.name}} ({{itens.size}} kb)</li>
    </ul>
    <!-- <h1>{{ caminhos[0].folder }}</h1> -->
  </div>
</template>

<script>
import Caminhos from "./services/caminhos";
export default {
  name: "app",
  data() {
    return {
      caminhos: null
    };
  },

  mounted() {
    Caminhos.listar().then(resposta => {
      this.caminhos = resposta.data;
    });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
