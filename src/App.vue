<template>
  <div class="flex flex-col items-center my-10">
    <h1>Reaction timer</h1>
    <button
      :disabled="isPlaying"
      @click="start"
      class="bg-red-400 p-4 disabled:bg-red-200"
    >
      Play
    </button>
    <BlockComponent v-if="isPlaying" @endTimer="endGame" :delay="delay" />
    <p v-if="showResults">Reaction time {{ reactionTime }}</p>
  </div>
</template>

<script>
import BlockComponent from "./components/BlockComponent.vue";
export default {
  name: "App",
  components: {
    BlockComponent,
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 500;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.reactionTime = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: 0,
    };
  },
};
</script>
