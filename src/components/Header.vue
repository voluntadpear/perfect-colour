<template>
  <header>
    <Heading :h="1">Perfect Colour</Heading>
    <p>How good is your eye?</p>
  </header>
</template>

<script lang="ts">
import { createComponent } from 'vue-function-api';
import Heading from './Heading';

export default createComponent({
  components: { Heading },
  setup() {
    const title = 'Perfect Colour';
  },
});
</script>

<style lang="stylus" scoped>
h1 {
  margin-bottom: 0;
}

p {
  margin-top: 0.5rem;
}
</style>
