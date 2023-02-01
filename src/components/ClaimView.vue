<template lang="pug">
.claimWrapper
  h1.claim Spacer
  p.subclaim
    | Begin your journey throught our amazing galaxy, and discover places
    | and discover places you never even heard of.
  p.subclaim
    | Type anything space-related to start.
</template>

<script>
export default {
  name: 'ClaimView',
};
</script>

<style lang="scss" scoped>
.claimWrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: white;
  max-width: 450px;

}
.claim {
    font-size: 50px;
    margin: 0;
    text-transform: uppercase;
}

.subclaim{
    margin: 25px 0 0 0 ;
    text-align: center;
    font-size: 20px;
}
</style>
