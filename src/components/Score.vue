<template>
  <div class="row score">
    <div class="">
      <span class="badge left">{{
        score
          ? "Votre score : " + score
          : "Tapez Entrer pour démarrer la partie"
      }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "score",
  data: function() {
    return {
      score: 101
    };
  } /*,
  created: function() {
    this.score++;
  }*/
};
</script>

<style scoped>
.score {
  width: 80%;
}
</style>
