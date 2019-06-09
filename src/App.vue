<template>
  <div id="app">
    <button id="show-modal" @click="setTrue">Show Modal</button>
    <Modal :show.sync="showModal" @change="onResultChange">
      <h3 slot="header">custom header</h3>
      <div slot="body">custom body</div>
    </Modal>
  </div>
</template>

<script>
  import Modal from './components/modal'

  export default {
    name: 'App',
    components: {
      Modal
    },
    data() {
      return {
        showModal: false
      }
    },
    methods: {
      setTrue() {
        this.showModal = true;
      },
      onResultChange(val) {
        this.showModal = val;
      }
    }
  }
</script>

<style>

</style>
