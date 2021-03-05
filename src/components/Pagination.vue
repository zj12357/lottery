<template>
  <div class="pagination-wrp">
    <div
      class=" prev"
      :class="{ disabled: currentPage === 1 }"
      @click="prev"
    ></div>

    <div
      v-for="item in list"
      :key="item.value"
      class="item"
      :class="{
        'ignore ignore-left': item.type === 'ignore-left',
        'ignore ignore-right': item.type === 'ignore-right',
        active: item.type === 'number' && item.value === currentPage,
      }"
      @click="handleItemClick(item)"
    >
      {{ item.type === "number" ? item.value : "" }}
    </div>

    <div
      class=" next"
      :class="{ disabled: currentPage === totalPage }"
      @click="next"
    ></div>
  </div>
</template>

<script>
export default {
  props: {
    totalPage: {
      type: Number,
      required: true,
    },
    currentPage: {
      type: Number,
      default: 1,
    },
  },
  data() {
    return {
      list: [],
      listGenerators: {
        total_page_lte_7: () => {
          this.list = [];
          for (let i = 1; i <= this.totalPage; i++) {
            this.list.push({ type: "number", value: i });
          }
        },
        current_page_lte_4: () => {
          this.list = [];
          for (let i = 1; i <= 6; i++) {
            this.list.push({ type: "number", value: i });
          }
          this.list.push({ type: "ignore-right", value: "&gt" });
          this.list.push({ type: "number", value: this.totalPage });
        },
        current_page_gte_last_4: () => {
          this.list = [];
          this.list.push({ type: "number", value: 1 });
          this.list.push({ type: "ignore-left", value: "&lt" });
          for (let i = this.totalPage - 5; i <= this.totalPage; i++) {
            this.list.push({ type: "number", value: i });
          }
        },
        middle: () => {
          this.list = [];
          this.list.push({ type: "number", value: 1 });
          this.list.push({ type: "ignore-left", value: "&lt" });
          for (let i = this.currentPage - 2; i <= this.currentPage + 2; i++) {
            this.list.push({ type: "number", value: i });
          }
          this.list.push({ type: "ignore-right", value: "&gt" });
          this.list.push({ type: "number", value: this.totalPage });
        },
      },
    };
  },
  mounted() {
    this.$watch(
      "currentPage",
      (newVal) => {
        // 对currentPage执行边界检测
        if (newVal < 1) {
          this.$emit("update:currentPage", 1);
          return;
        } else if (newVal > this.totalPage) {
          this.$emit("update:currentPage", this.totalPage);
          return;
        }
        this.genList();
      },
      {
        immediate: true,
      }
    );
    this.$watch("totalPage", (newVal) => {
      // 对totalPage执行边界检测
      if (newVal < 1) {
        this.totalPage = 1;
        return;
      }
      this.$emit("update:currentPage", 1);
      this.genList();
    });
  },
  methods: {
    /**
     * totalPage <= 7 要直接罗列，无需显示省略号
     *
     * totalPage > 7 则分类讨论，此时假设totalPage===100，分类如下：
     * currentPage在[1, 2, 3, 4]区间（即前4个）
     * currentPage在[5, 6, ..., 95, 96]
     * currentPage在[97, 98, 99, 100]区间（即后4个）
     *
     * 要注意：totalPage===8没有'middle'状态
     */
    genList() {
      if (this.totalPage <= 7) {
        this.listGenerators["total_page_lte_7"]();
        return;
      }
      if (this.currentPage <= 4) {
        this.listGenerators["current_page_lte_4"]();
      } else if (this.currentPage >= this.totalPage - 3) {
        this.listGenerators["current_page_gte_last_4"]();
      } else {
        this.listGenerators["middle"]();
      }
    },
    prev() {
      this.$emit("update:currentPage", this.currentPage -= 1);
      if (this.currentPage !== this.currentPage) {
        this.$emit("currentChange", this.currentPage);
      }
    },
    next() {
      this.$emit("update:currentPage", this.currentPage += 1);
      if (this.currentPage <= this.totalPage) {
        this.$emit("currentChange", this.currentPage);
      }
    },
    handleItemClick(item) {
      if (item.type === "number") {
        this.$emit("update:currentPage", item.value);
      } else if (item.type === "ignore-left") {
        this.$emit("update:currentPage", this.currentPage - 5);
      } else if (item.type === "ignore-right") {
        this.$emit("update:currentPage", this.currentPage + 5);
      }
       this.$emit("currentChange", item.value);
    },
  },
};
</script>

<style lang="scss" scoped>
@media screen and (min-width: 1200px) {
  .ob-ai-game-box {
    .pagination-wrp {
      display: flex;
      justify-content: center;
      align-items: center;
      .item {
        margin: 0 5px;
        background-image: url("../assets/images/content/page.png");
        background-size: 100%;
        background-position: center;
        background-repeat: no-repeat;
        color: #606266;
        min-width: 58px;
        border-radius: 2px;
        padding: 0 4px;
        display: inline-block;
        font-size: 24px;
        height: 58px;
        line-height: 58px;
        cursor: pointer;
        box-sizing: border-box;
        text-align: center;
        user-select: none;
        &:hover {
          color: #db5431;
        }
        &.active {
          background-image: url("../assets/images/content/page_active.png");
          color: #fff;
        }
      }
      .ignore {
        max-width: 58px;
        display: flex;
        justify-content: center;
        align-items: center;
        &::after {
          content: "···";
        }
        &-left:hover::after {
          content: "<<";
          font-size: 20px;
        }
        &-right:hover::after {
          content: ">>";
          font-size: 20px;
        }
      }
      .prev,
      .next {
        background: none;
        width: 12px;
        height: 20px;
        cursor: pointer;
        margin: 0 20px;
        &.disabled {
          cursor: not-allowed;
        }
      }
      .prev {
        background-image: url("../assets/images/content/page_prev.png");
        background-size: 100%;
        background-position: center;
        background-repeat: no-repeat;
      }
      .next {
        background-image: url("../assets/images/content/page_next.png");
        background-size: 100%;
        background-position: center;
        background-repeat: no-repeat;
      }
    }
  }
}
</style>
