<template>
  <h1>Super liste de courses</h1>
  <ol>
    <li v-for="(ing, index) in courses" :key="`ing${index}`">
      <div v-html="`${ing.title}${ing.quantitee}${ing.magasin}`"></div>
    </li>
  </ol>
</template>

<script setup>
import { ref } from "vue";

const byn = `<button type="button" @click="checked" v-show="buy">ckeck</button><hr />`;
const courses = ref([
  {
    title: "<h2>Eau évian</h2><br/>",
    quantitee: "<em>6 bouteilles</em><br/>",
    magasin: "<p>A chercher au <b>Lidl</b></p><br/>",
    checked: false
  },
  {
    title: "<h2>Oeufs</h2><br/>",
    quantitee: "<em>30 pièces</em><br/>",
    magasin: "<p>A chercher au <i>Super U</i></p><br/>",
    checked: false
  },
  {
    title: "<h2>latte macchiato dolce gusto</h2><br/>",
    quantitee: "<em>1 boite</em><br/>",
    magasin: "<p>A chercher au <ins>Cora</ins></p><br/>",
    checked: false
  },
  {
    title: "<h2>salade iceberg</h2><br/>",
    quantitee: "<em>3 têtes</em><br/>",
    magasin: "<p>A chercher au <b>Rewe</b></p><br/>",
    checked: false
  },
  {
    title: "<h2>batonnet pour les chats</h2><br/>",
    quantitee: "<em>10 paquets</em><br/>",
    magasin: "<p>A chercher au <i>Action</i></p><br/>",
    checked: false
  },
  {
    title: "<h2>poulet</h2><br/>",
    quantitee: "<em>500 g</em><br/>",
    magasin: "<p>A chercher au <ins>Aldi</ins></p><br/>",
    checked: false
  }
]);

const buy = ref(true);
const checked = () => {
  buy.value = false;
};
</script>
