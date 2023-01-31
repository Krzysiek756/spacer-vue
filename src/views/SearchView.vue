<template lang="pug">
.wrapper
    Claim
    Search
</template>

<style lang="scss" scoped>// ograniczone wyłącznie do tego komponentu
.wrapper {
  width: 100%;
  padding: 30px;
  height: 100vh;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-image: url('../assets/peakpx.jpg');
  background-size: cover;
  background-position: 50% 0;
  background-repeat: no-repeat;
}

</style>
// data w konponencie nie moze byc czystym obiektem
// jakaś wartość musi być zawsze inaczej nie bedzie ona reaktywna przy dekarowaniu dyrektywy
<script>

import axios from 'axios';
import debounce from 'lodash.debounce';
import Search from '@/components/SearchInput.vue';
import Claim from '@/components/ClaimView.vue';

const API = 'http://images-api.nasa.gov/search';

export default {
  name: 'SearchView',
  components: {
    Claim,
    Search,
  },
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
