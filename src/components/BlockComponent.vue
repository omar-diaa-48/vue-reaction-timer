<template>
  <div
    v-if="showBlock"
    class="
      w-96
      rounded-2xl
      bg-green-400
      text-white text-center
      px-0
      py-24
      mx-auto
      my-10
      cursor-pointer
    "
    @click="stopTimer"
  >
    <p>Click me</p>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endTimer", this.reactionTime);
    },
  },
};
</script>