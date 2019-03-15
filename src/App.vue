<template>
  <div id="app container"><joueur></joueur><game></game></div>
</template>

<script>
import Game from "./components/Game";
import Score from "./components/Score";
import Joueur from "./components/Joueur";
export default {
  name: "App",
  components: {
    Game,
    Score,
    Joueur
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 600px;
  display: block;
}
</style>
