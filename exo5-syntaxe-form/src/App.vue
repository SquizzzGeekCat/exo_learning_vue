<template>
  <form action="" @submit.prevent="sendForm">
    <input type="text" name="" id="" v-model="name" placeholder="nom" />
    <input type="email" name="" id="" v-model="mail" placeholder="email" />
    <textarea
      rows=""
      cols=""
      v-model="comm"
      placeholder="commentaire"
    ></textarea>
    <button type="submit" @click="sendComm">envoyer</button>
    <span v-show="messageShow">{{ message }}</span>
  </form>
  <div v-show="showComm">
    <h2>Résumé :</h2>
    <p><b>Nom : </b>{{ name }}</p>
    <p><b>Email: </b>{{ mail }}</p>
    <p><b>Commentaire: </b>{{ comm }}</p>
  </div>
</template>
<script setup>
import { ref, computed } from "vue";

const name = ref("");
const mail = ref("");
const comm = ref("");
const message = ref("Les trois champs doivent etre completer ! Nudle !!");
const messageShow = ref(false);
const showComm = ref(false);

const sendComm = computed(() => {
  if (name.value != "" && mail.value != "" && comm.value != "") {
    showComm.value = true;
    messageShow.value = false;
  } else {
    showComm.value = false;
    messageShow.value = true;
  }
});
</script>
<style scoped></style>
