<template>
    <div class="boss-box">
      <img :src="getBossImg(name)" :alt="getBossImg(name)">
      <h3 class="boss-name">{{ name }}</h3>
      <div class="kill-grid">
        <h4>Recorded Kills: {{ recorded_kills }}</h4>
        <h4 style="color: #c6ff6b">Recorded Guild Kills: {{ guild_kills }}</h4>
        <div class="guild-breakdown">
          <span class="alliance">Alliance {{ alliance_kills }}</span>
          <span class="horde">Horde {{ horde_kills }}</span>
        </div>
        <div class="guild-bar">
          <div class="alliance-fill fill" :style="{ width: leftWidth + '%'}"></div>
          <div class="horde-fill fill" :style="{ width: rightWidth + '%' }"></div>
        </div>
      </div>


      <h4 style="margin-left: 10px; margin-bottom:0px">Most Popular Compositions:</h4>


      <div class="comp-grid">
        <div class="tank-box">
          <h5 style="margin:2px">
            <span style="margin: 0px; padding: 0px">
              <img src="@/assets/roles/tank.png" alt="Tanks" style="vertical-align:sub; width: 18px; border-bottom: 0px">
              Tanks
            </span>
          </h5>
          <div class="popular-tank-box">
            <div v-for="(tankClass, index) in tank_comp" :key="index">
              <h6>
                <span style="margin: 0px; padding: 0px">
                <img :src="getClassImg(tankClass.name)" :alt="getClassImg(tankClass.name)" style="vertical-align:sub; width: 12px; border-bottom: 0px">
                {{ tankClass.name }}
               </span>
              </h6>
            </div>
            <h5 style="margin:10px">Used for 23% kills</h5>
          </div>          
        </div>


        <div class="healer-box">
          <h5 style="margin:2px">
            <span style="margin: 0px; padding: 0px">
              <img src="@/assets/roles/healer.png" alt="Tanks" style="vertical-align:sub; width: 18px; border-bottom: 0px">
              Healers
            </span>
          </h5>
          <div class="popular-healer-box">
            <div v-for="(healerClass, index) in healer_comp" :key="index">
              <h6>
                <span style="margin: 0px; padding: 0px">
                <img :src="getClassImg(healerClass.name)" :alt="getClassImg(healerClass.name)" style="vertical-align:sub; width: 12px; border-bottom: 0px">
                {{ healerClass.name }}
               </span>
              </h6>
            </div>
            <h5 style="margin:10px">Used for 42% kills</h5>
          </div>          
        </div>
      </div>
    </div>
</template>

<style>
.boss-box {
    border: 1px solid rgb(255, 128, 0);;
    margin: 10px;
    height: 700px;
    width: calc(100% - 20px);
    background-image: url('~@/assets/grey-background.jpg');
    background-position: top center;
    background-size: 1000px 500px;
    background-color: rgb(44, 44, 44);
}

.kill-grid {
  height: 125px;
  border: 1px solid #f8b700;
  margin: 10px;
  text-align: center;
}

.comp-grid {
  height: 90px;
  margin: 10px;
  text-align: center;
  display: flex;
}

h4 {
  margin-top: 10px;
  margin-left: 2px;
  font-family: SemplicitaPro;
  color: #ffffff;
  font-weight: 400;
  line-height: 5px;
}

h5 {
  margin-top: 2px;
  margin-left: 2px;
  font-family: SemplicitaPro;
  color: #ffffff;
  font-weight: 400;
  line-height: 5px;
  font-size: 16px;
  vertical-align: center;
}

h6 {
  font-family: SemplicitaPro;
  color: #ffffff;
  text-align: left;
  margin: 0px;
  padding: 0px;
  font-size: 14px;
}

.guild-breakdown {
  display: flex;
  justify-content: space-between;
}

.alliance {
  text-align: left;
  font-family: SemplicitaPro;
  color: #4b4eff;
  font-weight: 400;
  line-height: 10px;
  margin-left: 10px;
}

.horde {
  text-align: right;
  font-family: SemplicitaPro;
  color: #fd0000;
  font-weight: 400;
  line-height: 10px;
  margin-right: 10px;
}

.guild-bar {
  margin-top: 10px;
  height: 20px;
  display: flex;
  flex-direction: row;
  border: 1px solid #f8b700; 
}

.alliance-fill {
  background-color: rgb(83, 83, 245);
}

.horde-fill {
  background-color: rgb(255, 93, 93);
}

.tank-box {
  margin: 2px;
  flex-basis: calc(50% - 4px);
}

.popular-tank-box {
  margin-top: 2px;
  padding: 2px;
  border: 1px solid #0004ff
}

.healer-box {
  margin: 2px;
  flex-basis: calc(50% - 4px);
}

.popular-healer-box {
  margin-top: 2px;
  padding: 2px;
  border: 1px solid #00b627
}

.boss-box img {
    position: relative;
    top: 0;
    left: 0;
    width: 100%;
    height: 40%;
    object-fit: cover;
    border-bottom: 10px;
    border-bottom: 1px solid grey;
}

.boss-name {
  font-size: 1.20rem;
  font-family: Open Sans,Arial,Helvetica,sans-serif;
  color: #f8b700;
  text-shadow: 0 0 1px transparent, 0 1px 2px rgb(0 0 0 / 80%);
  font-weight: 400;
  margin-left: 10px;
  margin-top: 5px;
  margin-bottom: 10px;
}
</style>

<script>
  export default {
    props: ['name', 'recorded_kills', 'guild_kills', 'alliance_kills', 'horde_kills', 'tank_comp', 'healer_comp'],
    methods: {
      getBossImg(bossName) {
        return require('../assets/bosses/' + bossName.toLowerCase().replace(/\s/g, "") + '.jpg')
      },
      getClassImg(className) {
        return require('../assets/classes/' + className.toLowerCase().replace(/\s/g, "") + '.jpg')
      },
    },
    computed: {
      leftWidth() {
        const total = this.alliance_kills + this.horde_kills;
        return this.alliance_kills / total * 100000;
      },
      rightWidth() {
        const total = this.alliance_kills + this.horde_kills;
        return this.horde_kills / total * 100000;
      },
    },
  }
</script>
