<template>
  <div class="c-number-input">
    {{ value }}
    <input
      class="c-number-input__control"
      ref="rangeInputRef"
      type="range"
      :min="min"
      :max="max"
      :step="step"
      :value="value"
      @input="onInput"
    />
  </div>
</template>

<script lang="ts">
import { ref, createComponent, computed, Ref } from 'vue-function-api';
import { RequiredProp } from '../helpers/vue-types';

const isNumber = (n: any): n is number => {
  return typeof n === 'number';
};

export default createComponent({
  props: {
    min: RequiredProp<number>(Number),
    max: RequiredProp<number>(Number),
    value: RequiredProp<number>(Number),
    step: RequiredProp<number>(Number),
  },
  setup(props, { emit }) {
    const rangeInputRef: Ref<HTMLInputElement | null> = ref(null);

    const onInput = () => {
      const rangeInputEl = rangeInputRef.value;
      if (!(rangeInputEl instanceof HTMLInputElement)) return;

      emit('input', Number(rangeInputEl.value));
    };

    return { onInput, rangeInputRef };
  },
});
</script>

<style lang="stylus" scoped>
@require '../styles/vars';

.c-number-input {
  display: flex;
  align-items: stretch;
  position: relative;
  border: 1px solid $border-color;
  border-radius: 1rem;
  flex-direction: column;
  padding: 1rem;
  box-sizing: border-box;

  &__control {
    margin-top: 1rem;
    width: 100%;
  }
}
</style>
