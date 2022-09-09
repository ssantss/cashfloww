<template>
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

<script>
/* import SplashScreen from "./components /SplashScreen.vue";
 */ import { defineAsyncComponent } from "vue";
import SplashScreen from "./components/SplashScreen.vue";

export default {
  components: {
    SplashScreen,
    Home: defineAsyncComponent(
      /*       Se crea una promesa llamada Home, que lo que hace es crear un setTimeout para que
       la aplicacion cargue, se creala promesa y se resuelve trayendo el componente de la pagina a utilizar 
       en el template, se utiliza la etiqueta Suspense, que es predefinida por vue!, tenemos un default que es componente principal que se va a renderizar
       y tenemos el fallback que es la animacion para hacer la espera*/
      () =>
        new Promise((resolve) => {
          setTimeout(() => {
            resolve(import("./components/HomeVue.vue"));
          }, 2500);
        })
    ),
  },
};
</script>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
