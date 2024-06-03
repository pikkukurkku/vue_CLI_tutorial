<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if:="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja giveaway!</h1>
      <p>Grab your ninja gear!</p>
    </Modal>
  </teleport>
  <teleport to=".modals" v-if:="showModalTwo">
    <Modal theme="newYear" @close="toggleModalTwo">
      <template v-slot:buttons>
        <a href="https://portfolio-natalia-ogorek.adaptable.app/">portfolio</a>
        <a href="https://www.linkedin.com/in/natalia-ogorek--web-development/"
          >linked in</a
        >
      </template>
      <h1>Check me out!</h1>
      <p>I'm a full stack developer</p>
    </Modal>
  </teleport>

  <button @click="toggleModal">show modal</button>
  <button @click="toggleModalTwo">show my deets</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My first Vue App :)",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
      this.showModalTwo = false;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
      this.showModal = false;
    },
  },
};
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
  display: inline-block;
}
</style>
