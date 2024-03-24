<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    // LifeCycle Hooks[(beforeCreated, created)(beforeMounted, mounted)(beforeUpdated, updated)(beforeUnmounted, unmounted)]
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0
      }
    },
    mounted() {
      // console.log('component mounted')
      // fire a function after a certain amount of time
      setTimeout(() => {
        this.showBlock = true
        // console.log(this.delay)
        this.startTimer()
      }, this.delay)
    },
    methods: {
      startTimer() {
        this.timer = setInterval(() => {
          this.reactionTime += 10
          // console.log(this.timer)
        }, 10)
      },
      stopTimer() {
        clearInterval(this.timer)
        // console.log(this.reactionTime)
        // Emiting custom event
        this.$emit("end", this.reactionTime)
      }
    }
    // updated () {
    //   console.log('component updated')
    // },
    // unmounted() {
    //   console.log('unmounted')
    // }
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: wheat;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>