<script setup lang="ts">
import {format} from "date-fns";
const date = new Date();
const formattedDate = format(date, 'EEEE do MMMM')
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