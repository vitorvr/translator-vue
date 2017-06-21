<template>
  <div id="app" class="text-center">
    <br/>  
    <div class="col-md-6 col-md-offset-3 alert alert-dismissible alert-success">
      <h1>Translator</h1>
    </div>
    <TranslatorForm v-on:wordSubmited="translateWord"></TranslatorForm>
    <TranslatorOutput v-text="wordTranslated"></TranslatorOutput>
  </div>
</template>

<script>
import TranslatorForm from './components/TranslatorForm'
import TranslatorOutput from './components/TranslatorOutput'

export default {
  name: 'app',
  components: {
    TranslatorForm,
    TranslatorOutput
  },
  data: function () {
    return {
      wordTranslated: ''
    }
  },
  methods: {
    translateWord: function (text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170621T225307Z.0a69f5b27900ec75.863119260a6ce6bed0a16fa9b69b3b6561f57d79&lang=' + language + '&text=' + text)
        .then((response) => {
          console.log(response.url);
          this.wordTranslated = response.body.text[0];
        });
    }
  }
}
</script>

<style>
body {
  background: #FEFEFE;
}
</style>
