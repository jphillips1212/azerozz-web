<template>
  <div class="container">
    <azerozz-header></azerozz-header>

    <!-- NAV BAR -->
    <div>
      <nav>
        <a 
          href="#" 
          @mouseover="hover1=true" 
          @mouseleave="hover1=false" 
          :class="{active: selectedRaid === '10.0.5'}" 
          @click="setActive('10.0.5')"
        >
          <span :class="{raidText: !hover1, raidHoverText: hover1}">Vault of the Incarnates (10.0.5)</span>
        </a>
        <a 
          href="#" 
          @mouseover="hover2=true" 
          @mouseleave="hover2=false" 
          :class="{active: selectedRaid === '10.0.0'}" 
          @click="setActive('10.0.0')"
        >
          <span :class="{raidText: !hover2, raidHoverText: hover2}">Vault of the Incarnates (10.0.0)</span>
        </a>
      </nav>
      <div class="divider"></div>
    </div>
    <!-- END OF NAV BAR -->

    <vault-table></vault-table>
  </div>
</template>

<style>
  @font-face {
    font-family: SemplicitaPro;
    src: url(~@/assets/fonts/SemplicitaPro.otf)
  }
  .container {
    align-items: center;
    align-self: center;
    max-width: 100%;
    height: 100%;
    background-image: linear-gradient(rgba(255,255,255,0.4), rgb(15, 14, 2)), url('~@/assets/ulduar-background.jpg');
    background-repeat: no-repeat;
    background-position: top center;
    background-size: 2000px 1000px;
    background-color: rgb(15, 14, 2);
  }

  nav {
    display: flex;
    padding: 1rem;
  }

  a {
    text-decoration: none;
    transition: background-color 0.1s, color 0.1s;
    padding: 5px;
    margin-right: 20px;
  }

  a.active {
    background-color: #f8b700;
  }

  a.active span {
    color: black;
  }

  .raidText {
    font-family: Semplicita Pro, sans-serif;
    font-weight: 700;
    line-height: 1.5;
    color: #f8b700;
    cursor: pointer;
    padding: 6.6px, 10px;
    font-size: 1.2rem;
  }

  .raidHoverText {
    font-family: Semplicita Pro, sans-serif;
    font-weight: 700;
    line-height: 1.5;
    color: #000000;
    cursor: pointer;
    padding: 6.6px, 10px;
    font-size: 1.2rem;
  }

  a:hover {
    background-color: #f8b700;
    color: black;
  }

  .divider {
    height: 2px;
    background-color: black;
    margin-top: 0.2rem;
    margin-bottom: 2rem;
    margin-left: 1rem;
    margin-right: 2rem;
  }
</style>

<script>
import VaultTable from './components/VaultTable.vue'
import azerozzHeader from './components/AzerozzHeader.vue'

export default {
  name: 'App',
  components: {
    VaultTable,
    azerozzHeader
  },
  data() {
    return {
      selectedRaid: '10.0.5',
      hover1: false,
      hover2: false,
    }
  },
  methods: {
    setActive(raid) {
      this.selectedRaid = raid;
    },
  },
};

</script>