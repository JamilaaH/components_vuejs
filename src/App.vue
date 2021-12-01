<template>
  <div id="app">
    <div>
      <img src="./assets/pattern-curve.svg" id="coin-gauche">
      <img src="./assets/pattern-bg.svg" id="coin-droit">
      <img src="./assets/pattern-quotes.svg" id="milieu">
    </div>
    
    <transition name="slide-fade" v-for="carte, index in cartes "  :key="index" >
      <Avis  :texte="carte.texte" :auteur="carte.auteur" :metier="carte.metier" :img="carte.image" v-if="carte.show"/>
    </transition>
    <!-- <transition name="slide-fade">
      <AvisDeux v-if="slideDeux"/>
    </transition> -->

    <div class="bouton">
      <span @click="this.scroll" > <svg xmlns="http://www.w3.org/2000/svg" width="12" height="18"><path fill="none" stroke="#8585AC" stroke-width="3" d="M11 1L3 9l8 8"/></svg></span>
      <span @click="this.scroll" class="ml-2"> <svg xmlns="http://www.w3.org/2000/svg" width="13" height="18"><path fill="none" stroke="#8585AC" stroke-width="3" d="M2 1l8 8-8 8"/></svg></span>
    </div>

  </div>
</template>

<script>
import Avis from './components/Avis.vue'

export default {
  components: { Avis },
  name: 'App',
  data() {
    return {
      cartes : [
        {
          texte:"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc ac nulla lacus. Aenean fermentum leo id ultrices rutrum. Mauris venenatis enim vitae sodales malesuada. Proin metus libero, blandit congue consequat quis, semper sit amet diam.",
          auteur: "Tanya",
          metier: "UX Designer",
          image: require("@/assets/image-tanya.jpg"),
          show:true,
        },
        {
          texte:"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc ac nulla lacus. Aenean fermentum leo id ultrices rutrum. Mauris venenatis enim vitae sodales malesuada. Proin metus libero, blandit congue consequat quis, semper sit amet diam.",
          auteur: "Julien",
          metier: "Developpeur",
          image: require("@/assets/image-john.jpg"),
          show:false
        },
      ],
    }
  },
  methods : {
    scroll() {
      for (let index = 0; index < this.cartes.length; index++) {
        this.cartes[index].show = !this.cartes[index].show;
      }
  }
  }
}
</script>

<style>
html {
  overflow: hidden;
}
#app {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

#coin-gauche {
  position: absolute;
  bottom: 0;
  left: 0;
  z-index: -10;
}
#coin-droit {
  position: absolute;
  bottom: 0;
  right: 0;
  z-index: -10;

}
#milieu {
  position: absolute;
  bottom: 65vh;
  left: 10vw;
  z-index: -10;

}
.avatar {
  width: 70%;
  position: relative;
  box-shadow: 10px 5px 15px gray;
  border-radius: 5px;
  }
.text {
  font-size: 25px;
}

.bouton {
  background-color: white;
  box-shadow: 10px 5px 15px gray;  
  width: 5vw;
  padding: 7px 3px;
  border-radius: 15px;
  position: absolute;
  right: 40vw;
  bottom: 20vh;
  display: flex;
  justify-content: space-around;
}

/* Les animations d'entrée (« enter ») et de sortie (« leave »)  */
/* peuvent utiliser différentes fonctions de durée et de temps.  */
.slide-fade-enter-active {
  transition: all .5s ease-in;
}
.slide-fade-leave-active {
transition: all .1s ease-out;
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(100px);
  opacity: 0;
}
</style>
