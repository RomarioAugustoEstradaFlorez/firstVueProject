<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" /> -->
    <component v-bind:is="compToUse" v-bind="propsToUse"></component>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import { defineAsyncComponent } from "vue";

const helloAsyncWorld = defineAsyncComponent(
  () => import("../components/HelloWorld.vue")
);

@Options({
  components: {
    HelloWorld,
    helloAsyncWorld,
  },
})
export default class HomeView extends Vue {
  public compToUse = "helloAsyncWorld";
  public propsToUse = {
    msg: "Lo que sea",
  };
}
</script>
