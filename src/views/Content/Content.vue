<!-- Contnet -->
<template>
  <div class="ob-ai-game-content">
    <div class="ob-ai-game-content-ask"></div>
    <div class="ob-ai-game-content-main">
      <div class="ob-ai-game-content-main-banner">
        <div class="ob-ai-game-content-main-discount"></div>
      </div>
      <div class="ob-ai-game-content-main-text">
        <div
          class="ob-ai-game-content-main-text-item"
          v-for="item in textList"
          :key="item.id"
        >
          <p>{{ item.title }}</p>
          <p>{{ item.content }}</p>
        </div>
      </div>
      <div class="ob-ai-game-content-main-lottery">
        <div class="ob-ai-game-content-main-lottery_box">
          <img src="../../assets/images/lottery/box.png" alt="" />
        </div>
        <div class="ob-ai-game-content-main-lottery_btn">
          <div
            class="ob-ai-game-content-main-lottery_btn_item"
            @click="showLottery"
          >
            <img src="../../assets/images/lottery/start.png" alt="" />
          </div>
          <div
            class="ob-ai-game-content-main-lottery_btn_item"
            @click="handleOpen"
          >
            <img src="../../assets/images/lottery/redemption_code.png" alt="" />
          </div>
        </div>
      </div>
      <div class="ob-ai-game-content-main-boxs">
        <div class="ob-ai-game-content-main-boxs-title"></div>
        <div class="ob-ai-game-content-main-boxs-guns">
          <div
            class="ob-ai-game-content-main-boxs-guns-item"
            v-for="item in getBoxs(5)"
            :key="item.id"
          >
            <div class="ob-ai-game-content-main-boxs-guns-content">
              <div class="ob-ai-game-content-main-boxs-guns_bg bg_hover">
                <img :src="item.src" alt="" class="gun gun_hover " />
              </div>
              <div class="ob-ai-game-content-main-boxs-guns_text">
                {{ item.text }}
              </div>
            </div>
          </div>
        </div>
        <div class="ob-ai-game-content-main-boxs-guns">
          <div
            class="ob-ai-game-content-main-boxs-guns-item"
            v-for="item in getBoxs(4)"
            :key="item.id"
          >
            <div class="ob-ai-game-content-main-boxs-guns-content">
              <div class="ob-ai-game-content-main-boxs-guns_bg bg_hover">
                <img :src="item.src" alt="" class="gun gun_hover " />
              </div>
              <div class="ob-ai-game-content-main-boxs-guns_text">
                {{ item.text }}
              </div>
            </div>
          </div>
        </div>
        <div class="ob-ai-game-content-main-boxs-guns">
          <div
            class="ob-ai-game-content-main-boxs-guns-item"
            v-for="item in getBoxs(5)"
            :key="item.id"
          >
            <div class="ob-ai-game-content-main-boxs-guns-content">
              <div class="ob-ai-game-content-main-boxs-guns_bg bg_hover">
                <img :src="item.src" alt="" class="gun gun_hover " />
              </div>
              <div class="ob-ai-game-content-main-boxs-guns_text">
                {{ item.text }}
              </div>
            </div>
          </div>
        </div>
        <div class="ob-ai-game-content-main-boxs-guns">
          <div
            class="ob-ai-game-content-main-boxs-guns-item"
            v-for="item in getBoxs(4)"
            :key="item.id"
          >
            <div class="ob-ai-game-content-main-boxs-guns-content">
              <div class="ob-ai-game-content-main-boxs-guns_bg bg_hover">
                <img :src="item.src" alt="" class="gun gun_hover " />
              </div>
              <div class="ob-ai-game-content-main-boxs-guns_text">
                {{ item.text }}
              </div>
            </div>
          </div>
        </div>
        <div class="ob-ai-game-content-main-boxs-guns">
          <div
            class="ob-ai-game-content-main-boxs-guns-item"
            v-for="item in getBoxs(3)"
            :key="item.id"
          >
            <div class="ob-ai-game-content-main-boxs-guns-content">
              <div class="ob-ai-game-content-main-boxs-guns_bg bg_hover">
                <img :src="item.src" alt="" class="gun gun_hover " />
              </div>
              <div class="ob-ai-game-content-main-boxs-guns_text">
                {{ item.text }}
              </div>
            </div>
          </div>
        </div>
        <div class="ob-ai-game-content-main-boxs-page">
          <Pagination
            :totalPage="totalPage"
            :currentPage.sync="currentPage"
            @currentChange="changePage"
          ></Pagination>
        </div>

        <div class="ob-ai-game-content-main-boxs-poster01"></div>
        <div class="ob-ai-game-content-main-boxs-poster02"></div>
      </div>
      <div class="ob-ai-game-content-main-webp_01"></div>
      <div class="ob-ai-game-content-main-webp_02"></div>
    </div>
    <div class="ob-ai-game-content-lottery">
      <div class="ob-ai-game-content-lottery_box">
        <img src="../../assets/images/lottery/box.png" alt="" />
      </div>
      <div class="ob-ai-game-content-lottery_btn">
        <div class="ob-ai-game-content-lottery_btn_item" @click="showLottery">
          <img src="../../assets/images/lottery/start.png" alt="" />
        </div>
        <div class="ob-ai-game-content-lottery_btn_item" @click="handleOpen">
          <img src="../../assets/images/lottery/redemption_code.png" alt="" />
        </div>
      </div>
    </div>
    <div class="ob-ai-game-content-boxs">
      <div class="ob-ai-game-content-boxs-title"></div>
      <div class="ob-ai-game-content-boxs-guns">
        <div
          class="ob-ai-game-content-boxs-guns-item"
          v-for="item in boxsList"
          :key="item.id"
        >
          <div class="ob-ai-game-content-boxs-guns-item-content">
            <div class="ob-ai-game-content-boxs-guns_bg">
              <img :src="item.src" alt="" class="gun" />
            </div>
            <div class="ob-ai-game-content-boxs-guns_text">{{ item.text }}</div>
          </div>
        </div>
      </div>
      <div class="ob-ai-game-content-boxs-poster">
        <div class="ob-ai-game-content-boxs-poster-img">
          <img src="../../assets/images/lottery/poster.png" alt="" />
        </div>
        <div class="ob-ai-game-content-boxs-poster-webp_01"></div>
        <div class="ob-ai-game-content-boxs-poster-webp_02"></div>
      </div>
    </div>
    <Lottery
      :isShow="isShowLottery"
      @hide="hideLottery"
      @showWin="handleOpenGun"
    />
  </div>
</template>

<script>
import gun_m4 from "../../assets/images/lottery/gun_m4.png";
import Pagination from "@/components/Pagination";
import Lottery from "@/components/Lottery/Lottery";
export default {
  data() {
    return {
      textList: [
        {
          id: 1,
          title: "★ 注册俸禄",
          content:
            "注册成功后，即可开启注册俸禄宝箱1次，1个账号仅有1次 开启机会。",
        },
        {
          id: 2,
          title: "★ 邀请俸禄",
          content:
            "成功邀请1名会员并充值到达1钻石以上，即可获得开启邀请俸禄宝箱，每位会员只有1次机会为您添加。",
        },
        {
          id: 3,
          title: "★ 加群俸禄",
          content:
            "加入官方指定游戏群：XXXXX,即可向管理员领取开箱机会，每位会员只有1次领取机会。",
        },
        {
          id: 4,
          title: "★ 分享俸禄",
          content:
            "会员每天可在群内（XXX）分享1次欧皇体验（价值在30钻 石B)，并可以向管理员领取1次机会，1天只能领取1次。",
        },
        {
          id: 5,
          title: "★ 关注俸禄",
          content:
            " 关注官方媒体(XXX)即可活动1次开箱机会.关注官方媒体(XXX)即可活动1次开箱机会.",
        },
        {
          id: 6,
          title: "★ 精彩锦集",
          content:
            "将您在游戏中（XXXorXXX)发送给官方邮箱（XXXX@XXX.COM),一经采纳就可以获得抽奖机会。",
        },
        {
          id: 7,
          title: "★ 投放俸禄",
          content:
            "您可在各大直播平台直播、短视频平台投放我们官方抽奖的视频（配上文案）截图，即可获取1次抽奖机会。",
        },
        {
          id: 8,
          title: "★ 精彩锦集",
          content: "对于我们网站有极大帮助者即可获取我们官方赠送的特殊豪礼。",
        },
      ],
      boxsList: [],
      totalPage: 5,
      currentPage: 1,
      isShowLottery: false,
    };
  },
  components: {
    Pagination,
    Lottery,
  },
  created() {},
  mounted() {
    for (let index = 0; index < 20; index++) {
      this.boxsList.push({
        id: index,
        src: gun_m4,
        text: "0.55%",
      });
    }
  },
  methods: {
    getBoxs(num) {
      let boxs = [];
      for (let index = 0; index < num; index++) {
        boxs.push({
          id: index,
          src: gun_m4,
          text: "0.55%",
        });
      }
      return boxs;
    },
    handleOpen() {
      this.$emit("changeModal", true);
    },
    handleOpenGun(id) {
      this.$emit("changeModalGun", true, id);
    },
    changePage(page) {
      console.log(page);
    },
    showLottery() {
      this.isShowLottery = true;
    },
    hideLottery() {
      this.isShowLottery = false;
    },
  },
};
</script>
<style scoped lang="scss">
@media screen and (min-width: 1200px) {
  .ob-ai-game-box {
    .ob-ai-game-content {
      background-position: center 20px;
      background-size: 1920px;
      .ob-ai-game-content-ask {
        width: 855px;
        height: 153px;
        margin-top: 44px;
      }
      .ob-ai-game-content-main {
        width: 1360px;
        height: 3204px;
        background-size: 100% 100%;
        top: -79px;
        .ob-ai-game-content-main-banner {
          width: 1225px;
          height: 500px;
          background-image: url("../../assets/images/content/banner_bg_pc.png");
          margin-top: 114px;
        }
        .ob-ai-game-content-main-discount {
          width: 314px;
          height: 49px;
          bottom: 30px;
        }
        .ob-ai-game-content-main-text {
          flex-direction: row;
          flex-wrap: wrap;
          justify-content: center;
          width: 1200px;
          .ob-ai-game-content-main-text-item {
            width: 50%;
            padding: 0 20px;
            margin-bottom: 28px;
            p {
              font-size: 18px;
            }
          }
        }

        .ob-ai-game-content-main-lottery {
          height: 630px;
          background-image: url("../../assets/images/lottery/box_light.png");
          background-position: center -10px;
          background-repeat: no-repeat;
          background-size: 70%;
          display: flex;
          justify-content: center;
          align-items: center;
          flex-direction: column;
          .ob-ai-game-content-main-lottery_box {
            width: 283px;
            height: 210px;
            img {
              width: 100%;
              height: 100%;
            }
          }
          .ob-ai-game-content-main-lottery_btn {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: 75px;
            .ob-ai-game-content-main-lottery_btn_item {
              width: 306px;
              height: 90px;
              margin: 0 20px;
              cursor: pointer;
              img {
                width: 100%;
                height: 100%;
              }
            }
          }
        }
        .ob-ai-game-content-main-boxs {
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          position: absolute;
          z-index: 10;
          top: 1600px;
          .ob-ai-game-content-main-boxs-title {
            width: 314px;
            height: 49px;
            background-image: url("../../assets/images/lottery/boxs_title.png");
            background-size: 100%;
            background-repeat: no-repeat;
            background-position: center;
            margin-bottom: 46px;
          }
          .ob-ai-game-content-main-boxs-guns {
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            justify-content: center;
            width: 1238px;
            .ob-ai-game-content-main-boxs-guns-item {
              width: 20%;
              display: flex;
              justify-content: center;
              align-items: center;
              margin-bottom: 25px;
              .ob-ai-game-content-main-boxs-guns-content {
                width: 200px;
                height: auto;
                display: flex;
                justify-content: space-between;
                align-items: center;
                flex-direction: column;

                &:hover {
                  .bg_hover {
                    transition: all 0.4s ease;
                    .gun_hover {
                      top: 20px;
                    }
                  }
                }
                .ob-ai-game-content-main-boxs-guns_bg {
                  width: 198px;
                  height: 198px;
                  background-image: url("../../assets/images/lottery/gun_bg.png");
                  background-repeat: no-repeat;
                  background-size: 100%;
                  background-position: center;
                  cursor: pointer;

                  .gun {
                    display: block;
                    width: 198px;
                    height: auto;
                    position: relative;
                    top: 40px;
                    transition: all 0.4s ease;
                  }
                }
                .ob-ai-game-content-main-boxs-guns_text {
                  font-size: 16px;
                  color: #f00;
                  margin-top: 10px;
                }
              }
            }
          }
          .ob-ai-game-content-main-boxs-page {
            margin-top: 50px;
          }
          .ob-ai-game-content-main-boxs-poster01 {
            width: 469px;
            height: 444px;
            background-image: url("../../assets/images/content/poster_pc01.png");
            background-position: center;
            background-repeat: no-repeat;
            background-size: 100%;
            position: absolute;
            bottom: -37px;
            right: -242px;
          }
          .ob-ai-game-content-main-boxs-poster02 {
            width: 498px;
            height: 449px;
            background-image: url("../../assets/images/content/poster_pc02.png");
            background-position: center;
            background-repeat: no-repeat;
            background-size: 100%;
            position: absolute;
            bottom: -33px;
            left: -222px;
          }
        }
        .ob-ai-game-content-main-webp_01 {
          width: 412px;
          height: 329px;
          background-image: url("../../assets/images/content/webp_pc01.png");
          right: -285px;
          bottom: 1415px;
        }
        .ob-ai-game-content-main-webp_02 {
          width: 396px;
          height: 415px;
          background-image: url("../../assets/images/content/webp_pc02.png");
          left: -143px;
          bottom: 1351px;
        }
      }
      .ob-ai-game-content-lottery {
        display: none;
      }
      .ob-ai-game-content-boxs {
        display: none;
      }
    }
  }
}
.ob-ai-game-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-image: url("../../assets/images/content/content_bg.png");
  background-position: center 114px;
  background-repeat: no-repeat;
  background-size: 840px;
  background-color: #000;
  overflow: hidden;
  .ob-ai-game-content-ask {
    width: 678px;
    height: 121px;
    background-image: url("../../assets/images/content/ask_title_bg.png");
    background-position: center;
    background-repeat: no-repeat;
    background-size: 100%;
    margin-top: 23px;
  }
  .ob-ai-game-content-main {
    width: 639px;
    min-height: 1189px;
    background-image: url("../../assets/images/content/main_content_bg.png");
    background-position: center;
    background-repeat: no-repeat;
    background-size: 100% 100%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    position: relative;
    padding-bottom: 30px;
    .ob-ai-game-content-main-banner {
      width: 595px;
      height: 334px;
      background-image: url("../../assets/images/content/banner_bg.png");
      background-position: center;
      background-repeat: no-repeat;
      background-size: 100%;
      margin-top: 16px;
      position: relative;
    }
    .ob-ai-game-content-main-discount {
      width: 314px;
      height: 49px;
      background-image: url("../../assets/images/content/discount_title.png");
      background-position: center;
      background-repeat: no-repeat;
      background-size: 100%;
      margin-top: 16px;
      position: absolute;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
    }
    .ob-ai-game-content-main-text {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      flex-direction: column;
      width: 524px;
      .ob-ai-game-content-main-text-item {
        width: 100%;
        margin-bottom: 28px;
        p {
          font-size: 20px;
          width: 100%;
        }
        p:nth-child(1) {
          color: #d95538;
        }
        p:nth-child(2) {
          color: #989898;
        }
      }
    }
    .ob-ai-game-content-main-lottery {
      display: none;
    }
    .ob-ai-game-content-main-boxs {
      display: none;
    }
    .ob-ai-game-content-main-boxs-guns {
      display: none;
    }
    .ob-ai-game-content-main-webp_01 {
      width: 119px;
      height: 106px;
      position: absolute;
      z-index: 2;
      right: -53px;
      bottom: 213px;
      background-image: url("../../assets/images/content/webp_01.png");
      background-position: center;
      background-repeat: no-repeat;
      background-size: 100%;
    }
    .ob-ai-game-content-main-webp_02 {
      width: 168px;
      height: 176px;
      position: absolute;
      z-index: 2;
      left: -46px;
      bottom: 84px;
      background-image: url("../../assets/images/content/webp_02.png");
      background-position: center;
      background-repeat: no-repeat;
      background-size: 100%;
    }
  }
  .ob-ai-game-content-lottery {
    width: 100%;
    height: 500px;
    background: #262528;
    background-image: url("../../assets/images/lottery/box_light.png");
    background-position: center -86px;
    background-repeat: no-repeat;
    background-size: 70%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    .ob-ai-game-content-lottery_box {
      width: 283px;
      height: 210px;
      img {
        width: 100%;
        height: 100%;
      }
    }
    .ob-ai-game-content-lottery_btn {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-top: 75px;
      .ob-ai-game-content-lottery_btn_item {
        width: 306px;
        height: 90px;
        margin: 0 20px;
        cursor: pointer;
        img {
          width: 100%;
          height: 100%;
        }
      }
    }
  }
  .ob-ai-game-content-boxs {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 40px;
    .ob-ai-game-content-boxs-title {
      width: 314px;
      height: 49px;
      background-image: url("../../assets/images/lottery/boxs_title.png");
      background-size: 100%;
      background-repeat: no-repeat;
      background-position: center;
    }
    .ob-ai-game-content-boxs-guns {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      margin-top: 20px;
      .ob-ai-game-content-boxs-guns-item {
        width: 25%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 25px;
        .ob-ai-game-content-boxs-guns-item-content {
          width: 179px;
          height: 171px;
          display: flex;
          justify-content: space-between;
          align-items: center;
          flex-direction: column;
          .ob-ai-game-content-boxs-guns_bg {
            width: 150px;
            height: 150px;
            background-image: url("../../assets/images/lottery/gun_bg.png");
            background-repeat: no-repeat;
            background-size: 100%;
            background-position: center;
            .gun {
              display: block;
              width: 150px;
              height: auto;
              position: relative;
              top: 40px;
            }
          }
          .ob-ai-game-content-boxs-guns_text {
            font-size: 16px;
            color: #f00;
          }
        }
      }
    }
    .ob-ai-game-content-boxs-poster {
      width: 100%;
      height: 500px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      margin-top: 40px;
      .ob-ai-game-content-boxs-poster-img {
        width: 469px;
        height: 444px;
        img {
          width: 100%;
          height: 100%;
        }
      }
      .ob-ai-game-content-boxs-poster-webp_01 {
        width: 119px;
        height: 106px;
        position: absolute;
        z-index: 2;
        right: 0;
        top: 0;
        background-image: url("../../assets/images/lottery/webp_01.png");
        background-position: center;
        background-repeat: no-repeat;
        background-size: 100%;
      }
      .ob-ai-game-content-boxs-poster-webp_02 {
        width: 168px;
        height: 176px;
        position: absolute;
        z-index: 2;
        left: 8px;
        bottom: 160px;
        background-image: url("../../assets/images/lottery/webp_02.png");
        background-position: center;
        background-repeat: no-repeat;
        background-size: 100%;
      }
    }
  }
}
</style>
