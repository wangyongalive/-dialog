<template>
  <div id="modal">
    <transition name="modal"
                enter-active-class="animated bounceIn"
                leave-active-class="animated bounceOut"
    >
      <div class="modal-mask" v-show="myShow">
        <div class="modal-wrapper">
          <div class="modal-container">
            <div class="modal-header">
              <slot name="header">
                default header
              </slot>
            </div>
            <div class="modal-body">
              <slot name="body">
                body header
              </slot>
            </div>
            <div class="modal-footer">
              <button class="modal-button-left" @click="myShow = false"> 取消</button>
              <button class="modal-button-right" @click="myShow = false"> OK</button>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
  import animate from 'animate.css';

  export default {
    name: "modal",
    props: {
      show: {
        type: Boolean,
        required: true
      }
    },
    data() {
      return {
        myShow: this.show
      }
    },
    watch: {
      show(val) {
        this.myShow = val;  // 监听父组件的变化
      },
      myShow(val) {
        this.$emit("change", val); // 将变化通知父组件
      }
    },
  }
</script>

<style scoped>
  .modal-mask {
    background-color: rgba(0, 0, 0, .5);
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 99;

    display: flex;
    align-items: center; /*垂直居中*/
    justify-content:center;/*水平居中*/
  }

  .modal-container {
    background-color: white;
    width: 300px;
    padding: 20px 30px;
  }

  .modal-header {
    text-align: center;
    color: green;
  }

  .modal-body {
    margin: 20px 0;
    text-align: center;
    font-size: 14px;
  }

  .modal-footer{
    padding: 10px;
  }
  .modal-button-left {
    float: left;
    border: 0;
  }

  .modal-button-right {
    border: 0;
    float: right;
    background-color: green;
  }
</style>
