<template>
  <div class="content">
    <div class="row log">
      <p v-for="msg in collection" style="margin-top: 2px;">
        <span class="badge" style="float: none;"
          ><i class="material-icons">{{ icon }}</i
          >{{ msg }}</span
        >
      </p>
    </div>

    <div class="row game" @click.self="clickOnInterface">
      <span
        class="round animated pulse"
        @click.stop="clickOnRound"
        v-bind:style="roundStyle"
        :class="{
          bonus: activeBonus,
          badcolor: activateBadColor,
          zoomIn: animated,
          fadeIn: !animated
        }"
      ></span>
    </div>
    <div class="row score">
      <span class="badge" style="float: none;">Score : {{ click }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "score",
  data: function() {
    return {
      click: 0,
      roundStyle: {
        height: "50px",
        width: "50px",
        margin: "10% 50%"
      },
      activeBonus: false,
      activateBadColor: false,
      animated: false,
      collection: [],
      icon: ""
    };
  },
  created: function() {
    window.setInterval(
      this.updateRound,
      (Math.floor(Math.random() * 5) + 1) * 1000
    );
  },
  methods: {
    clickOnRound: function(event) {
      if (this.activeBonus && event.altKey) {
        this.click = this.click + 10;
        this.icon = "wb_iridescent";
        this.collection.unshift(" Excellent ! +10");
        this.updateRound();
        return;
      } else {
        this.click++;
        this.icon = "thumb_up";
        this.collection.unshift(" +1");
        this.updateRound();
      }
    },
    clickOnInterface: function(event) {
      this.click--;
      this.icon = "thumb_down";
      this.collection.unshift(" -1");
      this.updateRound();
    },
    updateRound: function() {
      this.animated = !this.animated;
      let size = Math.random() * (100 - 10) + 10;
      let top = Math.random() * (20 - 5) + 5;
      let left = Math.random() * (70 - 5) + 5;
      this.activeBonus = size > 80;
      this.activateBadColor = size < 20;
      this.roundStyle.width = `${size}px`;
      this.roundStyle.height = `${size}px`;
      this.roundStyle.margin = `${top}% ${left}%`;
    }
  }
};
</script>

<style scoped>
.row {
  margin-bottom: 0;
}
.content {
  height: 600px;
}
.game {
  width: 80%;
  height: 80%;
  display: block;
  background: #004d40;
}

.round {
  background: #ff1744;
  border-radius: 9999px;
  position: absolute;
}
.bonus {
  background: #ffff00;
}
.badcolor {
  background: #00695c;
}
.log {
  height: 35px; /**/
  width: 80%;
  background: #b2dfdb;
  overflow: hidden;
  text-align: center;
}
.score {
  width: 80%;
  background: #b2dfdb;
  text-align: center;
}
span.badge {
  font-size: 24px;
}
.log > p > span > i {
  position: relative;
  top: 4px;
}
</style>
