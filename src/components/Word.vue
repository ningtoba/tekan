<template>
  <div class="border-2">
    <div class="p-10 h-96 flex-col"> 
      <div class="text-center text-xl text-white flex">
        <div v-for="word in words" :key="word.index" class="ml-1 inactiveWords">
          <span v-for="letter in phrase(word)" :key="letter.index">{{letter}}</span>
        </div>
      </div>
      <div class="flex justify-center mt-5 text-white">
        <span class="border-2 p-4 rounded-2xl font-bold">{{author}}</span>
      </div>
      <div>
        <input v-model="keyInput" @keypress="activeWord(keyInput)"  type="text" class="w-full mt-5">
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Word',
  data() {
    return {
      content: null,
      author: null,
      words: [],
      alph: [],
      nextWord: String,
      keyInput: ''
    }
  },

  created() {
    axios.get('https://quote-garden.herokuapp.com/api/v3/quotes/random').then(response => (this.content = response.data.data[0].quoteText)).then(() => {
      this.words = this.content.split(' ')
    })
    axios.get('https://quote-garden.herokuapp.com/api/v3/quotes/random').then(response => (this.author = response.data.data[0].quoteAuthor))
  },

  methods: {
    phrase(text) {
      let test = text.split("")
      for (let value of test) {
        this.alph.push(value)
      }
      this.alph.push(' ')
      // console.log(this.words)
      // console.log(this.alph)

      return test
    },

    activeWord(keyInput) {
      if (keyInput !== '') {
        console.log(keyInput)
        keyInput = ''
        console.log(keyInput)
      }
      // for(let value of this.words) {
      //   if(keyInput === value[' ']) {
      //     value++
      //     console.log(value)
      //   }
      // }
      // console.log(keyInput)
    },

    keyCompare() {

    }
  }
}
</script>