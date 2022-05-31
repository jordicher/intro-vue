<template>
  <button ref="btn">click!</button>
</template>

<script>
import { ref, watch } from "vue";

export default {
  setup() {
    const btn = ref(null);
    console.log(btn.value); //* null

    watch(btn, (value) => {
      console.log(value); //* html
    });

    return {
      btn,
    };
  },
};
</script>
