<template>
  <div class="row" id="translatorForm">
    <div class="col-md-6 col-md-offset-3">
      <form id="translate" class="well form-inline" v-on:submit="translateSubmit">
        <input class="form-control" type="text" v-model="wordToTranslate" placeholder="Enter the word...">
        <select class="form-control" v-model="language">
          <option value="pt">Portuguese</option>
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="fr">French</option>
          <option value="de">German</option>
        </select>
        <input class="btn btn-success" type="submit" value="Translate">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translatorForm',
  data: function () {
    return {
      wordToTranslate: '',
      language: ''
    }
  },
  created: function () {
    this.language = 'pt';
  },
  methods: {
    translateSubmit: function (e) {
      this.$emit('wordSubmited', this.wordToTranslate, this.language);
      e.preventDefault();
    }
  }
}
</script>

<style>
  #translate {
    border-radius: 10px;
    border: 1px solid #ccc;
}
</style>
