<script setup lang="ts">
import {format} from "date-fns";

let formattedDate = ref();

const updateDate = () => {
  const date = new Date();
  formattedDate.value = format(date, 'EEEE do MMMM HH:mm:ss');
  setTimeout(() => updateDate(), 1000);
}

updateDate();
</script>

<template>
  <div>
    <h1>{{ formattedDate }}</h1>
  </div>
</template>

<style scoped>
h1 {
  font-family: "Baskerville Old Face", serif;
  user-select: none;
  -webkit-user-select: none;
  font-size: calc(5vw + 5vh);
}

div {
  padding: 0;
  margin: 0;
  width: 100vw;
  height: 100vh;
  background-color: beige;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>