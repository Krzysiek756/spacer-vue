<template lang="pug">
.searchWrapper
    label(for='serach') Search
    input(name='search' v-model="searchValue" @input="handleInput")#search
</template>

<script>
export default {
  name: 'SearchInput',
};
</script>

<style lang="scss" scoped>

  .searchWrapper {
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

</style>
