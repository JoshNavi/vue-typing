<template lang="html">
  <span>{{text}}<span class="blinking">|</span></span>
</template>

<script>
/**
 * Component documentation
 */
export default {
  name: 'vue-typing',
  data () {
    return {
      text: '',
      wordsIndex: 0,
      delay: 100
    }
  },
  computed: {
    currentWord () {
      return this.words[this.wordsIndex]
    }
  },
  props: {
    words: {
      type: Array,
      required: true
    }
  },
  mounted () {
    this.startTyping()
  },
  methods: {
    sleep (ms) {
      return new Promise(resolve => setTimeout(resolve, ms))
    },
    async startTyping () {
      while (true) {
        await this.typeWord()
        await this.sleep(500)
        this.wordsIndex = this.wordsIndex + 1
        if (this.wordsIndex >= this.words.length) {
          this.wordsIndex = 0
        }
      }
    },
    async typeWord () {
      var i
      for (i = 0; i <= this.currentWord.length; i++) {
        this.text = this.words[this.wordsIndex].substring(0, i)
        await this.sleep(this.delay)
      }
      await this.sleep(1000)
      for (i = this.currentWord.length; i >= 0; i--) {
        this.text = this.currentWord.substring(0, i)
        await this.sleep(this.delay)
      }
      return new Promise(resolve => resolve())
    }
  }
}
</script>

<style>
@keyframes blink {
  from, to {
    color: transparent;
  }
  50% {
    color: #000000;
  }
}

.blinking {
  -webkit-animation: 1s blink step-end infinite;
  -moz-animation: 1s blink step-end infinite;
  -ms-animation: 1s blink step-end infinite;
  -o-animation: 1s blink step-end infinite;
  animation: 1s blink step-end infinite;
}
</style>
