<template>
  <div id="app">
    <header>
      <span><img src="./assets/logo.png"  height="30" width="80" alt="Vue.js PWA"></span>
    </header>
    <main>
      <img src="./assets/logo1.png"  height="110" width="150" alt="Vue.js PWA">
      <hello></hello>
      <button class="btn_main" @click="showModal">Try Now</button>
      <Modal v-show="isModalVisible" @close="closeModal" />
    </main>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Modal from './components/Modal'

export default {
  name: 'app',
  components: {
    Hello, Modal
  },
  data() {
    return {
      isModalVisible: false
    };
  },
  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    }
  }
};

</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: center;
  margin-top: 40px;
}

header {
  margin: 0;
  height: 56px;
  padding: 0 16px 0 24px;
  background-color: #606b7f;
  color: #ffffff;
}

header span {
  display: block;
  position: relative;
  font-size: 20px;
  line-height: 0;
  letter-spacing: .02em;
  font-weight: 400;
  box-sizing: border-box;
  padding-top: 15px;
}
.btn_main{
  background:#41b883;
  color:#fff;
  border:none;
  position:relative;
  height:60px;
  font-size:1.6em;
  padding:0 2em;
  cursor:pointer;
  transition:800ms ease all;
  outline:none;
}
.btn_main:hover{
  background:#fff;
  color:#41b883;
}
.btn_main:before,.btn_main:after{
  content:'';
  position:absolute;
  top:0;
  right:0;
  height:2px;
  width:0;
  background: #41b883;
  transition:400ms ease all;
}
.btn_main:after{
  right:inherit;
  top:inherit;
  left:0;
  bottom:0;
}
.btn_main:hover:before,.btn_main:hover:after{
  width:100%;
  transition:800ms ease all;
}

</style>
