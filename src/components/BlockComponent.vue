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
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
  }
};
</script>