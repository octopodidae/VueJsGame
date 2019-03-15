<template>
  <div class="joueur row">
    <div class="">
      <form @submit.prevent="setPlayer" :class="{ hide: player }">
        <div class="input-field col s12">
          <input placeholder="" id="first_name" type="text" class="validate" />
          <label for="first_name">Votre nom de joueur</label>
          <button type="submit" class="btn teal darken-4">Jouer</button>
        </div>
      </form>
    </div>
    <div class="row">
      <p>
        <span
          class="badge left teal darken-4"
          style="color: white; font-weight: 900;"
          v-html="welcomeMessage"
          :class="{ hide: !player }"
        ></span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "joueur",
  data: function() {
    return {
      player: "",
      welcomeMessage: ""
    };
  },
  updated: function() {
    this.welcomeMessage = `Bienvenu <span>${this.player}</span> !`;
  },
  /*directives: {
    border: function(el, binding) {
      el.style.borderColor = binding.arg;
    }
   hide: function(el, binding, vnode) {
      let player = vnode.context.player;
      let isForm = vnode.tag === "form";
      if (isForm) {
        el.style.display = player ? "none" : "block";
      } else {
        el.style.display = player ? "block" : "none";
      }
    }
  },*/
  methods: {
    setPlayer: function(event) {
      let playerName = event.target[0].value;
      if (!playerName) {
        alert("Merci de renseigner votre pseudo !");
        return;
      }
      this.player = playerName;
    }
  }
};
</script>

<style scoped>
.hide {
  display: none;
}
.joueur {
  width: 80%;
}
</style>
