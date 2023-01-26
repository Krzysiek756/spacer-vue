<template lang="pug">
.wrapper
  .wrapper__search
    label(for='serach') Search
    input(name='search' v-model="searchValue" @input="handleInput")#search
    ul
      li(v-for='item in results' :key='item.data[0].nasa_id')
            p {{ item.data[0].description}}
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
import debounce from 'lodash.debounce';

const API = 'http://images-api.nasa.gov/search';

export default {
  name: 'SearchView',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },

  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>
