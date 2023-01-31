<template lang="pug">
.searchWrapper
    input(name='search' v-model="searchValue" @input="handleInput")#search
</template>

<script>
export default {
  name: 'SearchInput',
};
</script>

<style lang="scss" scoped>

  .searchWrapper {
    margin-top: 50px;
    width: 300px;
    display: flex;
    flex-direction: column;

  }

  input {
    height:30px;
    border: 0;
    border-bottom: 2px solid red;
    background: transparent;
    color: white;
    text-transform: uppercase;
  }

</style>
