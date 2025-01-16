<template>
  <input type="text" v-model="pseudo" placeholder="votre pseudo" />
  <br />
  <input type="password" v-model="pass" placeholder="le mot de passe !" />
  <br />
  <span :style="'color:red;'" v-if="pseudo || pass != ''">{{ message1 }}</span>

  <p v-show="pass != ''">Vous pouvez vous connecter</p>
  <button type="button" v-show="pass != ''" @click="greetings">
    Connexion
  </button>
  <!-- ATTENTION pas de .value dans le template -->
  <p v-show="result">"Hello administrator ! Good too see you!"</p>
</template>
<!-- v-show prend directe le resultat si c'est un boolean pas besoin de lui dire si cest true ou si cest false -->

<script setup>
import { computed, ref } from "vue";
const pass = ref("");
const pseudo = ref("");

const pwd = "qazwsx";
const id = "admin";

const message1 = "le pseudo et le mot de passe sont obligatoire";
const result = ref(false);
//Plutot que de vouloir retourner le resultat directement plutot le stocker dqns une variable
// et retourner la variable au template
const greetings = computed(() => {
  if (pass.value == pwd && pseudo.value == id) {
    result.value = true;
  } else {
    result.value = false;
  }
});
</script>

<style scoped></style>
