<template>
  <div>
      <div class="row">
              <p v-if="selectedplayer"><img style="width:50%" :src="selectedplayer" alt=""></p>
              <p v-if="selectedImage"><img style="width:50%" :src="selectedImage" alt=""></p>
      </div>
    <button @click="random()">Attack</button>
    <button @click="SPrandom()">SPAttack</button>
    <br/>
    moster hp{{mhp}}
    <br />
    player hp{{php}}
    <div v-if="mhp <= 0">
        player win
    </div>
    <div v-if="php <= 0">
        monster win
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
        monster : [
            'https://promotions.co.th/wp-content/uploads/2019/04/Thanos-Snap.jpg',
            'https://media.comicbook.com/2017/03/dragon-ball-z-cell-screen-shot-2017-03-09-at-113510-pm-237501.png',
            'data:image/jpeg;base64,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',
        ],
        player : [
            'https://cdn1.thr.com/sites/default/files/2019/10/star_wars-_episode_iii_-_revenge_of_the_sith_hayden_christensen.jpg',
            'https://mpics.mgronline.com/pics/Images/562000003115501.JPEG',
            'https://animeth-area.com/wp-content/uploads/2020/07/kzRvpKbUiONR3ZuM1QOX2I1g302.jpg',
        ],
        selectedImage: null,
        selectedplayer : null,
      ppower: "",
      mpoxer: "",
      php: 100,
      mhp: 100,
    };
  },
  methods: {
    random: function () {
      this.ppower = Math.floor(Math.random() * 7 + 3);
      this.mhp = this.mhp - this.ppower;
      this.mpower = Math.floor(Math.random() * 7 + 3);
      this.php = this.php - this.mpower;
    },
    SPrandom: function () {
      this.ppower = Math.floor(Math.random() * 10 + 5);
      this.mhp = this.mhp - this.ppower;
      this.mpower = Math.floor(Math.random() * 10 + 5);
      this.php = this.php - this.mpower;
    },
    randommonster (items) {
      return items[Math.floor(Math.random()*items.length)];
    },
    randomplayer (items) {
      return items[Math.floor(Math.random()*items.length)];
    },
  },
  created() {
    this.selectedImage = this.randommonster(this.monster)
    this.selectedplayer = this.randomplayer(this.player)
  }
};
</script>

<style>
</style>