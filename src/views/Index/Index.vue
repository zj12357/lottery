<template>
  <div class="ob-ai-game-box">
    <Header />
    <Content @changeModal="changeModal" @changeModalGun="changeModelGun" />
    <ModalCode :visible="codeVisible" @changeModal="changeModal" />
    <ModalGun
      :visible="gunVisible"
      @changeModal="changeModelGun"
      :lottery="gunId"
    />
  </div>
</template>
<script>
import Header from "../Header/Header";
import Content from "../Content/Content";
import ModalCode from "../../components/Modal/ModalCode";
import ModalGun from "../../components/Modal/ModalGun";

export default {
  name: "Index",
  data() {
    return {
      codeVisible: false,
      gunVisible: false,
      gunId: 0,
    };
  },
  components: {
    Header,
    Content,
    ModalCode,
    ModalGun,
  },
  mounted() {},
  methods: {
    changeModal(val) {
      this.codeVisible = val;
    },
    changeModelGun(val, id) {
      this.gunVisible = val;
      this.gunId = id;
    },
  },
};
</script>

<style lang="scss" scoped></style>
