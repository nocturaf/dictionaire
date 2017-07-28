<template>
  <div class="text-center" id="app">
    <h1>Dictionaire</h1>
    <h5>Translate a word instantly</h5>
    <br>
    <WordsForm v-on:formSubmit="doTranslate"></WordsForm>
    <WordsOutput v-text="translatedWord"></WordsOutput>
  </div>
</template>

<script>
import WordsForm from './components/WordsForm'
import WordsOutput from './components/WordsOutput'

export default {
  name: 'app',
  components: { WordsForm, WordsOutput },
  data: function()
  {
    return {
      translatedWord:''
    }
  },
  methods:{
    doTranslate:function(word, language)
    {
      this.$http.get(
        'https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170727T155307Z.6382aefd40db35fb.b748cdfb117f6160dd858f4a656fe4486f26fec3&lang='+language+'&text='+word
      ).then((response) => {
        this.translatedWord = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
  background-color:#fefefe;
  margin-top:100px;
  overflow-x:hidden;
}

h5,h6 {
  color: gray;
}
</style>