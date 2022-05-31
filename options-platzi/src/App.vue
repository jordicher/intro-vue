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

  <div>{{ baseUrl }}</div>
  <Home first-name="Jordi" last-name="Cher" other="otro" />

  <!-- En caso de que la variable estuviera en el mixin y en el componente, cogeria la del componente -->

  <Modal />

  <!--   <component :is="helloWorld"> </component>
 -->
  <!-- se renderiza a partir de un componente dinamico, solo lo podemos hacer en componentes que ya esten diponibles -->
</template>

<script>
import { defineAsyncComponent } from "vue";
import Menu from "./components/Menu.vue";
import Modal from "./components/Modal.vue";
import base from "@/mixins/base"; //arroba es para iniciar desde la carpeta src
import Home from "./components/Home.vue";

const HelloWorld = defineAsyncComponent(() =>
  import("./components/HelloWorld.vue")
);

export default {
  name: "App",
  components: {
    HelloWorld,
    Menu,
    Modal,
    Home,
  },
  mixins: [base],
  data() {
    return {
      helloWorld: HelloWorld,
      show: false,
    };
  },

  //beforeCreate Se llama cuando la instancia se inicializa, después de que las props se resuelven y antes de procesar opciones como data() o computed

  beforeCreate() {
    //código a ejecutar
    console.log("beforeCreate", this.$data, this.$el); //object, null
  },
  /* 
      created se llama cuando la instancia ha terminado de procesar todas las opciones relacionados con el estado, como lo son: datos reactivos, propiedades computadas, métodos y observadores, pero aún no comienza la fase de montado y la función $el aún no esta disponible.
   */
  created() {
    //lógica a ejecutar
    console.log("created", this.$data, this.$el); //proxy, null
  },

  /*  beforeMount Se llama cuando el componente ha sido montado, pero no existen nodos en el DOM aún, pero están a punto de ser ejecutado el render el DOM por primera vez, no se llama su usamos renderizado del lado de servidor. */

  beforeMount() {
    //lógica  a ejecutar
    console.log("beforeMount", this.$data, this.$el); //proxy, null
  },

  /* mounted Se llama cuando el componente ha sido montado, se considera montado cuando: todos sus componentes hijos síncronos han sido montados, no se incluyen los asíncronos o los que estén en modo suspendido < Suspense > , cuando su propio árbol del DOM ha sido creado e insertado en su contenedor padre.Tampoco es llamado durante renderizado del lado del servidor */

  mounted() {
    //logica a ejecutar
    console.log("mounted", this.$data, this.$el); //proxy, Elemento
  },

  /*  beforeUpdate Se llama justo cuando el componente esta por actualizar su árbol del DOM, debido a un cambio reactivo.Este hook se puede usar para acceder al DOM justo cuando Vue esta por hacer un cambio.
   */
  beforeUpdate() {
    //logica a ejecutar
  },

  /*updated Se llama justo cuando el componente ha sido actualizado por un cambio en su estado, En caso del padre su método se llamará cuando los métodos de sus hijos hayan terminado.Es importante tener cuidado si no somos precavidos podemos provocar ciclos de renderizado infinito. */

  updated() {
    //logica a ejecutar
  },

  /*beforeUnmount Se llama justo cuando la instancia esta por salir del DOM, cuando usamos este hook la instancia que esta por salir aun es funcional */

  beforeUnmount() {
    //logica a ejecutar
  },

  /*unmounted se llama cuando el componente es desmontado, un componente se considera desmontado cuando: todos su hijos han sido desmontados y todos sus efectos reactivos se han detenido, este hook se utiliza cuando queremos limpiar de manera manual algunos efectos como cuentas regresivas, conexiones con el server o eventos del DOM. */

  unmounted() {
    //logica a ejecutar
  },
};
</script>

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
