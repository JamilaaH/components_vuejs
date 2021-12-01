<template>
    <div class="container">
        <div class="row">
            <div class="col-6 text-left align-self-center">
                <p class="align-self-center text">{{texte}}</p>
                <p ><span class="fw-bold">{{auteur}}</span> {{metier}}</p>
            </div>
            <div class="col-6">
                <img :src=img alt="avatar" class="avatar">
            </div>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        texte: String,
        auteur: String, 
        metier: String,
        img : String,
    },
}
</script>

<style>
section {
  height: 60vh;

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


</style>
