<template lang="pug">
body
    .wrapper
            Claim
            Search
</template>

<style lang="scss" scoped>

@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800');

$font-weight-light:300;
$font-weight-normal:400;
$font-weight-bold:600;
$font-weight-black:800;

.wrapper {
  width: 100%;
  padding: 30px;
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  background-image: url('./assets/peakpx.jpg');
  background-size: cover;
  background-position: 50% 0;
  background-repeat: no-repeat;
}

*{
    box-sizing: border-box;
}

body {
    font-family: 'Montserrat', sans-serif;
    margin: -8px;
    padding: 0;

}

</style>

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
