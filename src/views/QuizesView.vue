<!-- @format -->

<!-- @format -->

<script setup>
// Importing quizes.json from data/quizes.json
import q from "../data/quizes.json";

// Importing ref for to bind the  state
import { ref, watch } from "vue";
import Card from "../components/Card.vue";

const quizes = ref(q); // all data is here
const search = ref(""); // input

// Every time listening on change in input field, passing through each quiz and keep if input have the same latter
watch(search, () => {
  quizes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
  // console.log("Helllo from Watch");
});
</script>

<template>
  <div>
    <header>
      <h1>Quizes</h1>

      <!-- "Trim" all whitespace -->
      <input v-model.trim="search" type="text" placeholder="Search..." />
    </header>

    <!-- Cards -->
    <div class="options-container">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>
header {
  display: flex;
  align-items: center;
  margin-top: 30px;
  margin-bottom: 10px;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
  color: royalblue;
}

header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}
</style>
