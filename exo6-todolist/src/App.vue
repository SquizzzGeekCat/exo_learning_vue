<template>
  <form action="" @submit.prevent="addTask">
    <input type="text" v-model="taskName" placeholder="Tache a faire" />
    <button :disabled="!taskName">Ajouter</button>
    <!-- pour rendre un bouton disabled use :disabled plus condition-->
  </form>
  <span v-show="mess">Tu na rien a faire ! </span>
  <ul>
    <li
      v-for="(t, index) in listTasks"
      :key="`t${index}`"
      :style="{ 'text-decoration-line': t.checked ? 'line-through' : 'none' }"
    >
      <input type="checkbox" @click="checkedTask(index)" />
      {{ t.title }}
    </li>
  </ul>
</template>

<script setup>
import { ref, computed } from "vue";
const date = new Date().toLocaleDateString();
const taskName = ref("");

const listTasks = ref([]);
const mess = ref(true);

const addTask = computed(() => {
  const newTask = { title: taskName.value, checked: false, dateAdded: date };
  listTasks.value.push(newTask);
  mess.value = false;
  taskName.value = "";
});

const checkedTask = (index) => {
  listTasks.value[index].checked = !listTasks.value[index].checked;
  console.log(listTasks.value[index].checked);
};
</script>

<style scoped>
form {
  border: 1px solid black;
  padding: 1em;
}
</style>
