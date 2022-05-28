<template>
  <div>
    <button @click="toggle">Modal</button>
    <teleport to="body">
      <!-- to => selector de css valido -->
      <div v-show="show">
        <h1>Titulo</h1>
        <p>Lorem Ipsum</p>

        <button @click="toggle">Cerrar</button>
      </div>
    </teleport>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
  },
};
</script>
