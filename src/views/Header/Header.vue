<template>
  <div class="ob-ai-game-header">
    <div class="ob-ai-game-header-logo">
      <div class="ob-ai-game-header-logo-img" @click="toIndex"></div>
    </div>
    <div class="ob-ai-game-header-tab">
      <div
        :class="[currentIndex === item.id ? headActive : headerItem]"
        v-for="item in tabList"
        :key="item.id"
        @click="changeTab(item.id)"
      >
        <div class="ob-ai-game-header-tab-item-icon">
          <img :src="item.icon" alt="" />
        </div>
        <p class="ob-ai-game-header-tab-item-text">{{ item.text }}</p>
      </div>
    </div>
  </div>
</template>
<script>
import icon_1 from "@/assets/images/tab/icon_1.png";
import icon_2 from "@/assets/images/tab/icon_2.png";
import icon_3 from "@/assets/images/tab/icon_3.png";
import icon_4 from "@/assets/images/tab/icon_4.png";
import icon_5 from "@/assets/images/tab/icon_5.png";
import icon_6 from "@/assets/images/tab/icon_6.png";
import icon_7 from "@/assets/images/tab/icon_7.png";
import icon_8 from "@/assets/images/tab/icon_8.png";
export default {
  name: "Header",
  data() {
    return {
      tabList: [
        {
          id: 1,
          icon: icon_1,
          text: "注册俸禄",
        },
        {
          id: 2,
          icon: icon_2,
          text: "加群俸禄",
        },
        {
          id: 3,
          icon: icon_3,
          text: "关注俸禄",
        },
        {
          id: 4,
          icon: icon_4,
          text: "精彩俸禄",
        },
        {
          id: 5,
          icon: icon_5,
          text: "邀请俸禄",
        },
        {
          id: 6,
          icon: icon_6,
          text: "分享俸禄",
        },
        {
          id: 7,
          icon: icon_7,
          text: "投放俸禄",
        },
        {
          id: 8,
          icon: icon_8,
          text: "贡献俸禄",
        },
      ],
      currentIndex: 1,
      headActive: "active ob-ai-game-header-tab-item",
      headerItem: "ob-ai-game-header-tab-item",
    };
  },
  mounted() {},
  methods: {
    changeTab(index) {
      this.currentIndex = index;
    },
    toIndex() {
      // if (history.length > 2) {
      //     window.history.go(-1);
      //   } else {
      //     window.location.href = "/";
      //   }
      window.location.href = "http://ai-pc.zbitcloud.com";
    },
  },
};
</script>

<style lang="scss" scoped>
@media screen and (min-width: 1200px) {
  .ob-ai-game-box {
    .ob-ai-game-header {
      width: 100%;
      height: 132px;
      justify-content: center;
      .ob-ai-game-header-logo {
        width: 111px;
        height: 112px;
        .ob-ai-game-header-logo-img {
          width: 100%;
          height: 100%;
          background-image: url("../../assets/images/header_logo_pc.png");
        }
      }
      .ob-ai-game-header-tab {
        justify-content: center;
        margin-left: 38px;
        .ob-ai-game-header-tab-item {
          width: 126px;
          height: 100px;
          &:hover {
            background-image: url("../../assets/images/header_active.png");
            background-position: center;
            background-repeat: no-repeat;
            background-size: 100%;
          }
          .ob-ai-game-header-tab-item-icon {
            width: 41px;
            height: 41px;
          }
          .ob-ai-game-header-tab-item-text {
            font-size: 20px;
            margin-top: 16px;
          }
        }
      }
    }
  }
}
.ob-ai-game-header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 236px;
  background-color: #1d1c21;
  .ob-ai-game-header-logo {
    width: 226px;
    display: flex;
    justify-content: center;
    align-items: center;
    .ob-ai-game-header-logo-img {
      width: 137px;
      height: 167px;
      background-image: url("../../assets/images/header_logo.png");
      background-position: center;
      background-repeat: no-repeat;
      background-size: 100%;
      cursor: pointer;
    }
  }
  .ob-ai-game-header-tab {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-wrap: wrap;
    .ob-ai-game-header-tab-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      width: 25%;
      height: 118px;
      cursor: pointer;
      &:active {
        background-image: url("../../assets/images/header_active.png");
        background-position: center;
        background-repeat: no-repeat;
        background-size: 100%;
      }
      &.active {
        background-image: url("../../assets/images/header_active.png");
        background-position: center;
        background-repeat: no-repeat;
        background-size: 100%;
      }
      .ob-ai-game-header-tab-item-icon {
        width: 41px;
        height: 41px;
        img {
          width: 100%;
          height: auto;
        }
      }
      .ob-ai-game-header-tab-item-text {
        font-size: 20px;
        color: #fff;
        margin-top: 16px;
      }
    }
  }
}
</style>
