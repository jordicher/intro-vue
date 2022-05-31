<template>
  <div>{{ firstName }}</div>
</template>

<script>
import { toRefs, computed } from "vue";

export default {
  props: {
    firstName: {
      type: String,
      default: "John",
      required: true,
    },
    lastName: {
      type: String,
      default: "Doe",
      required: true,
    },
  },
  setup(props, { attr, expose }) {
    const { firstName, lastName } = toRefs(props);

    const fullName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    //los atributos son los que no estan como props. En este caso other.
    console.log(attr);
    expose({
      //este valor podria ser accedido desde otros compoenntes!
      fullName,
    });

    return {
      fullName,
    };
  },
};
</script>
