<template>
  <div>
    <button @click="reloadPage()" class="btn btn-dark">NewGame</button>
    <div class="row">
        <div class="col-5">
          <img style="width:50%" :src="selectedplayer.img"  alt="">
        </div>
        <div class="col-2">
          <div class="row">
            <br>
            <br>
          </div>
          <div class="row">
            <img style="width:100%" :src="versus"  alt="">
          </div>
        </div>
        <div class="col-5">
          <img style="width:50%" :src="selectedmonster"  alt="">
    </div>
    </div>
    <div class = "row">
      <div class = "col-6" >
        Player : {{selectedplayer.name}}
        <br>
         <img  v-bind:style="{width: php + 'px'}"  :src="phpbar"  alt="" height="15px">
         {{php}}
      </div>
      <div class = "col-6">
        Monster
        <br>
        <img  v-bind:style="{width: mhp + 'px'}"  :src="mhpbar"  alt="" height="15px">
        {{mhp}}
      </div>
    </div>
    <br/>
    <br/>
    <button @click="random()" v-bind:disabled = "end"  class="btn btn-dark" >Attack</button>{{space}}
    <button @click="SPrandom()" v-bind:disabled = "end" class="btn btn-dark" >SPAttack</button>
    <div id="result">
      <div v-if="mhp==0 || php==0">
        <div v-if="mhp <php">       
        Player win
    </div>
    <div v-else-if="php < mhp">
        Monster win
    </div>
    <div v-else-if="mhp==php">
        Draw
    </div>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      end : false,
      space : "",
      phpbar : 'https://i.imgur.com/Q5xIoUa.png',
      mhpbar : 'https://i.imgur.com/Q5xIoUa.png',
      versus : 'https://www.freepngimg.com/thumb/animation/84267-versus-of-wallpaper-diagram-computer-witcher-geralt.png',
        monster : [
            'https://i.imgur.com/zh8nwSc.png',
            'https://vignette.wikia.nocookie.net/overlordmaruyama/images/8/88/Shalltear_Armor.png/revision/latest?cb=20190519235811',
            'https://i.imgur.com/3pJwcGt.png',
        ],
        player : [
          {name : "Mikasa",img :'https://i.imgur.com/KYwWZwg.png'},
            {name : "Cinderella",img : 'https://i.imgur.com/phQcqkZ.png'},
            {name : "2B",img : 'https://i.imgur.com/YkskKOi.png'},
        ],
        selectedmonster: {name:"",img:null},
        selectedplayer : {name:"",img:null},
      ppower: "",
      mpower: "",
      php: 250,
      mhp: 250,
      term: false,
    };
  },
  methods: {
    reloadPage : function(){
    window.location.reload()
  },
    random: function () {
      this.ppower = Math.floor(Math.random() * 7 + 3);
      this.mhp = this.mhp - this.ppower;
      if(this.php<=0){
        this.php = 0
        this.end = true
      }else if(this.mhp<=0){
        this.mhp = 0
        this.end = true
      }else if(this.mhp<=0&&this.php<=0){
        this.mhp = 0
        this.php = 0
      }
      this.mpower = Math.floor(Math.random() * 7 + 3);
      this.php = this.php - this.mpower;
      if(this.php<=0){
        this.php = 0
        this.end = true
      }else if(this.mhp<=0){
        this.mhp = 0
        this.end = true
      }else if(this.mhp<=0&&this.php<=0){
        this.mhp = 0
        this.php = 0
      }
    },
    SPrandom: function () {
      this.ppower = Math.floor(Math.random() * 10 + 5);
      this.mhp = this.mhp - this.ppower;
      if(this.php<=0){
        this.php = 0
        this.end = true
      }else if(this.mhp<=0){
        this.mhp = 0
        this.end = true
      }else if(this.mhp<=0&&this.php<=0){
        this.mhp = 0
        this.php = 0
      }
      this.mpower = Math.floor(Math.random() * 10 + 5);
      this.php = this.php - this.mpower;
      if(this.php<=0){
        this.php = 0
        this.end = true
      }else if(this.mhp<=0){
        this.mhp = 0
        this.end = true
      }else if(this.mhp<=0&&this.php<=0){
        this.mhp = 0
        this.php = 0
      }
    },
    randommonster (items) {
      return items[Math.floor(Math.random()*items.length)];
    },
    randomplayer (items) {
      return items[Math.floor(Math.random()*items.length)];
    },
  },
  created() {
    this.selectedmonster = this.randommonster(this.monster)
    this.selectedplayer = this.randomplayer(this.player)
  },
  
};
</script>

<style>
#result{
  height : 50px;
  font-size : 200%;
  color :aliceblue;
}
</style>