<!-- ModalCode -->
<template>
  <div class="ob-ai-gaming-modal-code" v-if="visible">
    <div class="ob-ai-gaming-modal-content">
      <p class="ob-ai-gaming-modal-content-title">输入兑换码</p>
      <div class="ob-ai-gaming-modal-content-input">
        <input type="text" />
      </div>
      <p class="ob-ai-gaming-modal-content-text-err"></p>
      <div class="ob-ai-gaming-modal-content-btn">
        <div
          class="ob-ai-gaming-modal-content-return"
          @click="handleColse"
        ></div>
        <div
          class="ob-ai-gaming-modal-content-confrim"
          @click="handleColse"
        ></div>
      </div>
      <div class="ob-ai-gaming-modal-content-close" @click="handleColse"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    visible: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {};
  },
  created() {},
  mounted() {},
  methods: {
    handleColse() {
      this.$emit("changeModal", false);
    },
  },
};
</script>
<style scoped lang="scss">
@media screen and (min-width: 1200px) {
  .ob-ai-game-box {
    .ob-ai-gaming-modal-code {
      .ob-ai-gaming-modal-content {
        width: 654px;
        height: 383px;
        .ob-ai-gaming-modal-content-title {
          font-size: 28px;
          text-shadow: 2px 3px 0 rgba(0, 0, 0, 0.3);
          margin-bottom: 13px;
        }
        .ob-ai-gaming-modal-content-input {
          width: 423px;
          height: 85px;
          input {
            padding: 0 30px;
            font-size: 20px;
          }
        }
        .ob-ai-gaming-modal-content-text-err {
          font-size: 18px;
        }
        .ob-ai-gaming-modal-content-btn {
          margin-top: 24px;
          .ob-ai-gaming-modal-content-return,
          .ob-ai-gaming-modal-content-confrim {
            width: 189px;
            height: 55px;
          }
        }
        .ob-ai-gaming-modal-content-close {
          right: 66px;
          top: 61px;
          width: 25px;
          height: 24px;
        }
      }
    }
  }
}
.ob-ai-gaming-modal-code {
  position: fixed;
  z-index: 999;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  .ob-ai-gaming-modal-content {
    width: 654px;
    height: 383px;
    background-image: url("../../assets/images/modal/modal_bg.png");
    background-position: center;
    background-size: 100%;
    background-repeat: no-repeat;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    position: relative;
    .ob-ai-gaming-modal-content-title {
      font-size: 28px;
      font-weight: 800;
      color: #fff;
      text-shadow: 2px 3px 0 rgba(0, 0, 0, 0.3);
      text-align: center;
      margin-bottom: 13px;
    }
    .ob-ai-gaming-modal-content-input {
      width: 423px;
      height: 85px;
      background-image: url("../../assets/images/modal/input_bg.png");
      background-position: center;
      background-size: 100%;
      background-repeat: no-repeat;
      input {
        width: 100%;
        height: 100%;
        background-color: transparent;
        border: none;
        outline: none;
        padding: 0 30px;
        font-size: 20px;
        color: #000;
      }
    }
    .ob-ai-gaming-modal-content-text-err {
      font-size: 18px;
      color: #ff4c4c;
      text-align: center;
    }
    .ob-ai-gaming-modal-content-btn {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
      margin-top: 24px;
      .ob-ai-gaming-modal-content-return {
        width: 189px;
        height: 55px;
        background-image: url("../../assets/images/modal/return.png");
        background-position: center;
        background-repeat: no-repeat;
        background-size: 100%;
      }
      .ob-ai-gaming-modal-content-confrim {
        width: 189px;
        height: 55px;
        background-image: url("../../assets/images/modal/confrim.png");
        background-position: center;
        background-repeat: no-repeat;
        background-size: 100%;
      }
    }
    .ob-ai-gaming-modal-content-close {
      position: absolute;
      right: 66px;
      top: 61px;
      z-index: 10;
      width: 25px;
      height: 24px;
      background-image: url("../../assets/images/modal/close_icon.png");
      background-position: center;
      background-repeat: no-repeat;
      background-size: 100%;
      cursor: pointer;
    }
  }
}
</style>
