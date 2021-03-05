<!-- Lottery -->
<template>
  <div class="ob-ai-lottery-box" v-if="isShow">
    <div class="ob-ai-lottery-content">
      <div class="ob-ai-lottery-content-scorll">
        <GameScroll
          :data="LotteryList"
          :class-option="optionLeft"
          class="seamless-warp"
          ref="game"
          @close="close"
          :isClose="true"
          :winningIndex="winningIndex"
        >
          <ul class="seamless-warp-container">
            <div
              class="ob-ai-lottery-content-scorll-item"
              v-for="item in LotteryList"
              :key="item.id"
              :style="{ backgroundImage: `url(${item.src})` }"
            >
              <div class="ob-ai-lottery-content-scorll-gun">
                <img src="../../assets/images/lottery/gun_m4.png" alt="" />
              </div>
              <p class="ob-ai-lottery-content-scorll-text">{{ item.text }}</p>
              <p class="ob-ai-lottery-content-scorll-des">
                {{ item.id + item.des }}
              </p>
            </div>
          </ul>
        </GameScroll>
      </div>
      <div class="ob-ai-lottery-content-scorll-blue_line"></div>
    </div>
  </div>
</template>

<script>
import cyan from "../../assets/images/lottery/cyan.png";
import fuchsia from "../../assets/images/lottery/fuchsia.png";
import pink from "../../assets/images/lottery/pink.png";
import purple from "../../assets/images/lottery/purple.png";
import blue from "../../assets/images/lottery/blue.png";
import yellow from "../../assets/images/lottery/yellow.png";

import GameScroll from "../vue-seamless-scroll";
export default {
  props: {
    isShow: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      LotteryList: [
        {
          id: 1,
          src: cyan,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
        {
          id: 2,
          src: fuchsia,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
        {
          id: 3,
          src: pink,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
        {
          id: 4,
          src: purple,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
        {
          id: 5,
          src: blue,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
        {
          id: 6,
          src: yellow,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
        {
          id: 7,
          src: yellow,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
        {
          id: 8,
          src: yellow,
          text: "格洛克 18 型 | 远光灯",
          des: "(崭新出厂)",
        },
      ],

      optionLeft: {
        direction: 2, //  1 往上 2向左
        limitMoveNum: 2,
        step: 44, // 每一帧的大小
        stepWidth: 220, // 横版的每一个子项的宽度
      },
      winningIndex: 4, //中奖的下标
    };
  },
  components: {
    GameScroll,
  },

  watch: {
    isShow(val) {
      if (val === true) {
        this.start();
      }
    },
  },
  created() {},
  mounted() {},
  methods: {
    start() {
      setTimeout(() => {
        this.optionLeft.step = 22;
      }, 1500);
    },
    close() {
      this.$emit("hide");
      this.$emit("showWin", this.winningIndex);
      this.optionLeft.step = 44;
    },
  },
};
</script>
<style scoped lang="scss">
@media screen and (min-width: 1200px) {
  .ob-ai-game-box {
    .ob-ai-lottery-box {
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
      .ob-ai-lottery-content {
        width: 1299px;
        height: 500px;
        background-image: url("../../assets/images/lottery/lottery_bg.png");
        background-size: 100%;
        background-repeat: no-repeat;
        background-position: center;
        box-shadow: 0 0 20px rgba($color: #ccc, $alpha: 0.7);
        padding: 125px 0;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        position: relative;
        .seamless-warp {
          overflow: hidden;
          width: 100%;
          height: 250px;
          .seamless-warp-container {
            display: flex;
            align-items: center;
          }
        }
        .ob-ai-lottery-content-scorll {
          width: 100%;
          height: 250px;
          display: flex;
          justify-content: flex-start;
          align-items: center;
          .ob-ai-lottery-content-scorll-item {
            width: 220px;
            height: 250px;
            background-size: 100% 100%;
            background-repeat: no-repeat;
            background-position: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            flex-shrink: 0;
            .ob-ai-lottery-content-scorll-gun {
              width: 159px;
              height: 95px;
              margin-top: 60px;
              img {
                width: 100%;
                height: auto;
              }
            }
            .ob-ai-lottery-content-scorll-text {
              font-size: 16px;
              color: #fff;
              margin-top: 24px;
              text-align: center;
            }
            .ob-ai-lottery-content-scorll-des {
              font-size: 14px;
              color: #fff;
              text-align: center;
              margin-top: 14px;
            }
          }
        }
        .ob-ai-lottery-content-scorll-blue_line {
          width: 47px;
          height: 279px;
          position: absolute;
          left: 50%;
          top: 50%;
          transform: translate(-50%, -50%);
          background-image: url("../../assets/images/lottery/lottery_line.png");
          background-position: center;
          background-repeat: no-repeat;
          background-size: 100% 100%;
          z-index: 10;
        }
      }
    }
  }
}
.ob-ai-lottery-box {
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
  .ob-ai-lottery-content {
    width: 100%;
    height: 500px;
    background-image: url("../../assets/images/lottery/lottery_bg.png");
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    box-shadow: 0 0 20px rgba($color: #ccc, $alpha: 0.7);
    padding: 125px 0;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    position: relative;
    .seamless-warp {
      overflow: hidden;
      width: 100%;
      height: 250px;
      .seamless-warp-container {
        display: flex;
        align-items: center;
      }
    }
    .ob-ai-lottery-content-scorll {
      width: 100%;
      height: 250px;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      .ob-ai-lottery-content-scorll-item {
        width: 220px;
        height: 250px;
        background-size: 100% 100%;
        background-repeat: no-repeat;
        background-position: center;
        display: flex;
        flex-direction: column;
        align-items: center;
        flex-shrink: 0;
        .ob-ai-lottery-content-scorll-gun {
          width: 159px;
          height: 95px;
          margin-top: 60px;
          img {
            width: 100%;
            height: auto;
          }
        }
        .ob-ai-lottery-content-scorll-text {
          font-size: 14px;
          color: #fff;
          margin-top: 24px;
          text-align: center;
          width: 154px;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
        .ob-ai-lottery-content-scorll-des {
          font-size: 12px;
          color: #fff;
          text-align: center;
          margin-top: 14px;
          width: 120px;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
      }
    }
    .ob-ai-lottery-content-scorll-blue_line {
      width: 47px;
      height: 279px;
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      background-image: url("../../assets/images/lottery/lottery_line.png");
      background-position: center;
      background-repeat: no-repeat;
      background-size: 100% 100%;
      z-index: 10;
    }
  }
}
</style>
