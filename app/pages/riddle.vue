<script setup lang="ts">
const {data, status, error, refresh, clear} = useFetch("https://riddles-api-eight.vercel.app/logic")

const answerShown = ref(false);
const questionReady = computed(() => {
  return status.value == 'success' && answerShown.value == false;
});

function showAnswer() {
  answerShown.value = true;
}

function newRiddle() {
  refresh();
  answerShown.value = false;
}

</script>

<template>
  <ClientOnly>
    <div>
      <h1 :class="{hidden: answerShown || !questionReady}">{{ data.riddle }}</h1>
      <button v-on:click="showAnswer" :class="{hidden: answerShown}"
              class="group transition-all italic">
        <span
            class="bg-left-bottom bg-gradient-to-r from-black to-black bg-[length:0%_5px] bg-no-repeat group-hover:bg-[length:100%_5px] transition-all duration-500 ease-out">
          {{ status == 'pending' ? "Loading" : "Show answer" }}
        </span>
      </button>
      <h1 :class="{ hidden: !answerShown}" class="answer">{{ data.answer }}</h1>
      <button v-on:click="newRiddle" :class="{hidden: !answerShown}"
              class="group transition-all italic">
        <span
            class="bg-left-bottom bg-gradient-to-r from-black to-black bg-[length:0%_5px] bg-no-repeat group-hover:bg-[length:100%_5px] transition-all duration-500 ease-out">
          New riddle
        </span>
      </button>
    </div>
  </ClientOnly>
</template>

<style scoped>
.hidden {
  display: none;
}

button {
  font-size: calc(3vw + 3vh);
  font-family: "Baskerville Old Face", serif;
  font-weight: bold;
}

h1 {
  font-family: "Baskerville Old Face", serif;
  user-select: none;
  -webkit-user-select: none;
  font-size: calc(3vw + 3vh);
  font-weight: bold;
  flex-basis: 100%;
  text-align: center;
}

div {
  padding: 0;
  margin: 0;
  width: 100vw;
  min-height: 100vh;
  height: 100%;
  background-color: beige;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}
</style>