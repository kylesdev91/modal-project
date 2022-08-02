<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <Spinner />
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">SIGN UP NOW</a>
        <a href="#">MORE INFO</a>
      </template>
      <h1>Ninja Giveaway!</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up to the Newsletter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </teleport>

  <button @click.shift="toggleModal">open modal (shift click)</button>
  <button @click="toggleModalTwo">open modal 2</button>
</template>

<script>
import Modal from './components/Modal';
import Spinner from './components/Spinner.vue';

export default {
  name: 'App',
  components: { Modal, Spinner },
  data() {
    return {
      title: 'My First Vue App!',
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
