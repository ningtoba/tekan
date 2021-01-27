<template>
  <div class="border-2">
    <div class="p-10 h-96 flex-col"> 
      <div class="text-center text-xl text-white flex">
        <div v-for="word in words" :key="word.index" class="ml-1">
          <span v-for="letter in phrase(word)" :key="letter.index">{{letter}}</span>
        </div>
      </div>
      <div class="flex justify-center mt-5 text-white">
        <span class="border-2 p-4 rounded-2xl font-bold">{{author}}</span>
      </div>
      <div>
        <input type="text" class="w-full mt-5">
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Word',
  data() {
    return{
      content: null,
      author: null,
      words: [],
      alph: []
    }
  },

  created() {
    axios.get('https://api.quotable.io/random').then(response => (this.content = response.data.content)).then(() => {
      this.words = this.content.split(' ')
    })
    axios.get('https://api.quotable.io/random').then(response => (this.author = response.data.author))
  },

  methods: {
    phrase(text) {
      let test = text.split("")
      for (let value of test) {
        this.alph.push(value)
      }
      this.alph.push(' ')
      return test
    },
    keyCompare() {

    }
  }
}
</script>