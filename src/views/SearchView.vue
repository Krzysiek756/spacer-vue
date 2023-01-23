<template lang="pug">
.wrapper
  .wrapper__search
    label(for='serach') Search
    input(name='search'
    v-model="searchValue"
    @input="handleInput")#search
</template>

<style lang="scss" scoped>// ograniczone wyłącznie do tego komponentu
.wrapper {
  width: 100%;
  padding: 30px;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;

  &__search {
    width: 300px;
    display: flex;
    flex-direction: column;

  }

  label {
    font-family: Montserrat, sans-serif;
  }

  input {
    height:30px;
    border: 0;
    border-bottom: 2px solid black;
  }

}
</style>
// data w konponencie nie moze byc czystym obiektem
// jakaś wartość musi być zawsze inaczej nie bedzie ona reaktywna przy dekarowaniu dyrektywy
<script>

import axios from 'axios';

const API = 'http://images-api.nasa.gov/search';

export default {
  name: 'SearchView',
  data() {
    return {
      searchValue: '',
    };
  },

  methods: {
    handleInput() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          console.table(response);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
