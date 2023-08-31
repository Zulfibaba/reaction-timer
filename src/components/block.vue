<template>
  <div class="block-outline" v-if="!showblock" >Click Here asap the block appears</div>
  <div class="block" v-if="showblock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],

  data() {
    return {
      showblock: false,
      timer: null,
      reactionTimer: 0,
    };
  },

  mounted() {
    setTimeout(() => {
      this.showblock = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        {
          this.reactionTimer += 10;
        }
      }, 10);
    },

    stopTimer() {
      clearInterval(this.timer);
      this.$emit("End", this.reactionTimer);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
.block-outline {
  width: 400px;
  border: solid 3px #0faf87;
  border-radius: 20px;
  background: transparent;
  color: #0faf87;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>