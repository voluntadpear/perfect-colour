<template>
  <div :style="style" class="rect"></div>
</template>

<script lang="ts">
import Vue from 'vue';
import { createComponent, computed } from 'vue-function-api';
import { RequiredProp } from '../helpers/vue-types';

type ColorRectSize = 's' | 'l';
const SIZE_TO_REM = (size: ColorRectSize): string => {
  switch (size) {
    case 's':
      return '1rem';
    case 'l':
      return '5rem';
  }
};

export default createComponent({
  props: {
    color: {
      type: String,
      required: true,
    },
    size: RequiredProp<ColorRectSize>(String),
  },
  setup(props) {
    const style = computed(() => {
      const { size = 'l' } = props;
      return {
        background: props.color,
        width: SIZE_TO_REM(size),
        height: SIZE_TO_REM(size),
      };
    });

    return { style };
  },
});
</script>

<style scoped>
.rect {
  display: inline-block;
  border-radius: 20%;
  border: 1px black solid;
}
</style>
