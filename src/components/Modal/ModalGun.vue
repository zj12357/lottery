<!-- ModalGun -->
<template>
  <div class="ob-ai-gaming-modal-gun" v-if="visible">
    <div class="ob-ai-gaming-modal-gun-box">
      <div class="ob-ai-gaming-modal-gun-bg">
        <div class="ob-ai-gaming-modal-gun-left">
          <img src="../../assets/images/modal/modal_gun.png" alt="" />
        </div>
        <div class="ob-ai-gaming-modal-gun-right">
          <p class="ob-ai-gaming-modal-gun-right-tilte">
            {{ lottery }}崭新出厂
          </p>
          <p class="ob-ai-gaming-modal-gun-right-des">格洛克18型｜远光灯</p>
          <div class="ob-ai-gaming-modal-gun-right-input">
            <div class="ob-ai-gaming-modal-gun-right-input-item">
              <p>类型</p>
              <span>手枪</span>
            </div>
            <div class="ob-ai-gaming-modal-gun-right-input-item">
              <p>外观</p>
              <span>
                崭新出厂
              </span>
            </div>
            <div class="ob-ai-gaming-modal-gun-right-input-item">
              <p>品质</p>
              <span>
                高级
              </span>
            </div>
          </div>
          <p class="ob-ai-gaming-modal-gun-right-price">0.13</p>
          <div class="ob-ai-gaming-modal-gun-right-pay">
            <div class="ob-ai-gaming-modal-gun-right-gun_put">
              放入背包
            </div>
            <div class="ob-ai-gaming-modal-gun-right-gun_return">
              <p>
                兑换价格（ <span>99.99<i class="price"></i></span> ）
              </p>
            </div>
          </div>
        </div>
      </div>
      <div
        class="ob-ai-gaming-modal-gun-close close_hover"
        @click="handleClose"
      ></div>
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
    lottery: {
      type: Number,
      required: false,
    },
  },
  data() {
    return {};
  },
  created() {},
  mounted() {},
  watch: {
    lottery(val) {
      this.lottery = val;
    },
  },
  methods: {
    handleClose() {
      this.$emit("changeModal", false);
    },
  },
};
</script>
<style scoped lang="scss">
@media screen and (min-width: 1200px) {
  .ob-ai-game-box {
    .ob-ai-gaming-modal-gun {
      .ob-ai-gaming-modal-gun-box {
        .ob-ai-gaming-modal-gun-bg {
          width: 750px;
          height: 581px;
          top: 0;
          left: 0;
          .ob-ai-gaming-modal-gun-left {
            width: 256px;
            height: 312px;
            margin-top: 70px;
            margin-left: 60px;
            img {
              width: 206px;
              height: auto;
            }
          }
          .ob-ai-gaming-modal-gun-right {
            margin-top: 90px;
            margin-left: 30px;
            .ob-ai-gaming-modal-gun-right-tilte {
              font-size: 18px;
            }
            .ob-ai-gaming-modal-gun-right-des {
              font-size: 22px;
              margin-top: 23px;
            }
            .ob-ai-gaming-modal-gun-right-input {
              margin-top: 30px;
              .ob-ai-gaming-modal-gun-right-input-item {
                width: 260px;
                height: 42px;
                border-bottom: 1px solid rgba(255, 255, 255, 0.2);
                p {
                  font-size: 14px;
                }

                span {
                  font-size: 16px;
                }
              }
            }
            .ob-ai-gaming-modal-gun-right-price {
              font-size: 36px;
              margin-top: 27px;
              &::before {
                width: 28px;
                height: 28px;
                margin-right: 8px;
              }
            }
            .ob-ai-gaming-modal-gun-right-pay {
              margin-top: 43px;
              right: 30px;
              .ob-ai-gaming-modal-gun-right-gun_put {
                width: 115px;
                height: 55px;
                font-size: 20px;
                line-height: 55px;
              }
              .ob-ai-gaming-modal-gun-right-gun_return {
                width: 243px;
                height: 55px;
                font-size: 20px;
                line-height: 55px;

                i {
                  width: 20px;
                  height: 16px;
                  margin-left: 2px;
                }
              }
            }
          }
        }
        .ob-ai-gaming-modal-gun-close {
          width: 25px;
          height: 24px;
          background-size: 11px 11px;
          right: 55px;
          top: 68px;
        }
      }
    }
  }
}
.ob-ai-gaming-modal-gun {
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
  .ob-ai-gaming-modal-gun-box {
    position: relative;
    animation: show-gun 0.3s ease-in-out;
    .ob-ai-gaming-modal-gun-bg {
      width: 750px;
      height: 581px;
      background-image: url("../../assets/images/modal/modal_gun_bg.png");
      background-position: center;
      background-size: 100%;
      background-repeat: no-repeat;
      top: 0;
      left: 0;
      z-index: 3;
      display: flex;
      justify-content: space-between;
      align-items: flex-start;

      .ob-ai-gaming-modal-gun-left {
        width: 256px;
        height: 312px;
        background-image: url("../../assets/images/modal/modal_gun_purple.png");
        background-position: center;
        background-size: 100%;
        background-repeat: no-repeat;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 70px;
        margin-left: 60px;
        img {
          width: 206px;
          height: auto;
        }
      }
      .ob-ai-gaming-modal-gun-right {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: flex-start;
        flex: 1;
        margin-top: 90px;
        margin-left: 30px;
        .ob-ai-gaming-modal-gun-right-tilte {
          font-size: 18px;
          color: #ff553e;
        }
        .ob-ai-gaming-modal-gun-right-des {
          font-size: 22px;
          color: #1decff;
          margin-top: 23px;
        }
        .ob-ai-gaming-modal-gun-right-input {
          margin-top: 30px;
          .ob-ai-gaming-modal-gun-right-input-item {
            position: relative;
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 260px;
            height: 42px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            p {
              color: #cacbea;
              font-size: 14px;
            }

            span {
              display: block;
              color: #1decff;
              font-size: 16px;
            }
          }
        }
        .ob-ai-gaming-modal-gun-right-price {
          font-size: 36px;
          color: #1decff;
          display: flex;
          align-items: center;
          margin-top: 27px;
          &::before {
            display: block;
            content: "";
            background-image: url("../../assets/images/modal/modal_member.png");
            background-position: center;
            background-repeat: no-repeat;
            background-size: 100%;
            width: 28px;
            height: 28px;
            margin-right: 8px;
          }
        }
        .ob-ai-gaming-modal-gun-right-pay {
          margin-top: 43px;
          display: flex;
          align-items: center;
          position: relative;
          right: 30px;
          .ob-ai-gaming-modal-gun-right-gun_put {
            width: 115px;
            height: 55px;
            background-image: url("../../assets/images/modal/gun_put.png");
            background-size: 100%;
            background-position: center;
            background-repeat: no-repeat;
            font-size: 20px;
            color: #fff;
            text-align: center;
            line-height: 55px;
            cursor: pointer;
          }
          .ob-ai-gaming-modal-gun-right-gun_return {
            width: 243px;
            height: 55px;
            background-image: url("../../assets/images/modal/gun_return.png");
            background-size: 100%;
            background-position: center;
            background-repeat: no-repeat;
            font-size: 20px;
            color: #000;
            text-align: center;
            line-height: 55px;
            cursor: pointer;
            p {
              display: flex;
              align-items: center;
              justify-content: center;
            }
            span {
              display: flex;
              align-items: center;
              justify-content: center;
            }
            i {
              display: block;
              width: 20px;
              height: 16px;
              background-image: url("../../assets/images/modal/gun_price_icon.png");
              background-size: 100%;
              background-position: center;
              background-repeat: no-repeat;
              margin-left: 2px;
            }
          }
        }
      }
    }
    .ob-ai-gaming-modal-gun-close {
      width: 25px;
      height: 24px;
      background-image: url("../../assets/images/modal/modal_gun_close.png");
      background-repeat: no-repeat;
      background-size: 11px 11px;
      background-position: center;
      position: absolute;
      z-index: 30;
      right: 55px;
      top: 68px;
      cursor: pointer;
      transition: all 0.4s ease;
    }
    // .close_hover:hover {
    //   transform: rotate(180deg);
    // }
  }
}
@keyframes show-gun {
  from {
    transform: scale(0.7, 0.7);
    visibility: hidden;
    opacity: 0;
  }
  to {
    transform: scale(1, 1);
    visibility: visible;
    opacity: 1;
  }
}
</style>
