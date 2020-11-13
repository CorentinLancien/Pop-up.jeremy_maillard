<template>
  <div class="app">
    <div class="button_container">
      <button id="button_popup" @mouseover="openModal()">
        Accéder à l'oeuvre
      </button>
    </div>

    <div id="modal" class="modaux">
      <h1>Un problème est survenu</h1>
      <h3>Veuillez réessayer</h3>
      <button class="close" @click="openModal()">
        Fermer et accéder à l'oeuvre
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  methods: {
    //Les fonctions
    //Fonction qui renvoie une couleur aléatoire
    getRandomColor() {
      //Code Hexadecimal
      var letters = "0123456789ABCDEF";

      //Prefixe dans le css pour annoncer une couleur en code hexadécimal
      var color = "#";
      //Pour i allait de 0 a 6 on prend une valeur random dans les lettres hexadécimales
      for (var i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    },
    //fonction qui renvoie un nombre aléatoire entre le minimum et le maximum .
    getRandomNumber(min, max) {
      return Math.random() * (max - min) + min;
    },

    // Ouvre la première pop-up
    openModal() {

      var modal =  document.getElementById("modal");
      var btn_popup = document.getElementById("button_popup");

      var randomTop = this.getRandomNumber(0, 550);
      var randomLeft = this.getRandomNumber(0, 1000);


      modal.style.top = randomTop + "px";
      modal.style.left = randomLeft + "px";
      modal.style.display = "block";
      modal.style.backgroundColor = this.getRandomColor();
      btn_popup.disabled = true;
      btn_popup.style.cursor = "wait";
    },
  },
};
</script>

<style>
body {
  padding: 0;
  margin: 0;
  background-color: #f2f1ef;
}

.button_container {
  width: 100%;
  text-align: center;
}

#button_popup {
  height: 50px;
  width: 300px;
  background-color: #4ecdc4;
  color: #ffffff;
  font-family: Helvetica;
  font-size: 20px;
  border: none;
  cursor: pointer;
  margin-top: 200px;
}

.modaux {
  display: none;
  height: 300px;
  width: 40%;
  background-color: #ffffff;
  font-family: helvetica;
  text-align: center;
  color: white;
  position: absolute;
  z-index: 20px;
  top: 25%;
  left: 25%;
  bottom: 25%;
  right: 25%;
  transition: 0.75;
}

.modaux h1 {
  padding-top: 60px;
}

.close {
  height: 60px;
  width: 300px;
  background-color: #4ecdc4;
  color: #ffffff;
  font-family: Helvetica;
  font-size: 20px;
  border: none;
  cursor: pointer;
}

.container {
  width: 100%;
}
</style>