<template>
  <Navbar />
  <MainVue />
  <ModalVue />
</template>

<script>
import Navbar from './components/Navbar.vue';
import MainVue from './components/Main.vue';
import ModalVue from './components/Modal.vue';
export default {
  components: {
    Navbar,
    MainVue,
    ModalVue,
  },
  setup(){

  }

}
</script>

<style>

</style>