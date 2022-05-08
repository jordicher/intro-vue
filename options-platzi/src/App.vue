<script>
import { defineAsyncComponent } from "vue";
import Menu from "./components/Menu.vue";

const HelloWorld = defineAsyncComponent(() =>
  import("./components/HelloWorld.vue")
);

export default {
  name: "App",
  components: {
    HelloWorld,
    Menu,
  },
  data() {
    return {
      helloWorld: HelloWorld,
      show: false,
    };
  },
};
</script>

<template>
  <header>
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <nav>
    <button @click="show = !show">Menu</button>
    <transition name="fade">
      <Menu v-show="show" />
    </transition>
    <!-- The difference is that an element with v-show will
    always be rendered and remain in the DOM; v-show only toggles the display
    CSS property of the element. -->
  </nav>

  <!--   <component :is="helloWorld"> </component>
 -->
  <!-- se renderiza a partir de un componente dinamico, solo lo podemos hacer en componentes que ya esten diponibles -->
</template>

<style>
@import "./assets/base.css";

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
</style>
