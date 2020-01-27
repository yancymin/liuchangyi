<template>
  <div class="nav">
    <div class="left">{{isCN?lang.CN[0]:lang.EN[0]}}</div>
    <div class="right">
      <div class="links">
        <a target="_blank" href="https://dribbble.com/Charlie_Liu">Dribbble</a>/
        <a target="_blank" href="http://designercharlie.zcool.com.cn/">Zcool</a>/
        <a target="_blank" href="https://www.instagram.com/liuchang_charlie/">Instagram</a>/
        <a target="_blank" href="https://weibo.com/u/2609433155">Weibo</a>
      </div>
      <a @click="langSwitch()" class="langSwitch">{{isCN?'CN':'EN'}}</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nav',
  props: ['isCN'],
  data() {
    return {
      lang: {
        CN: ['刘畅燚', 'CN'],
        EN: ['Charlie Liu', 'EN'],
      },
    };
  },
  methods: {
    langSwitch() {
      this.$emit('langBtn', false);
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../style/global.scss';

.nav {
  z-index: 99;
  width: 100vw;
  padding: 32px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  .left {
    @include font(18, 400, 18);
  }

  .right {
    display: flex;
    align-items: center;

    .links {
      a {
        margin: 4px;
        @include font(14, 400, 14);
        transition: all 0.25s ease;

        &:hover {
          text-decoration: underline;
        }
      }
    }

    .langSwitch {
      cursor: pointer;
      display: flex;
      justify-content: center;
      align-items: center;
      width: 36px;
      height: 36px;
      border: 1px solid #000000;
      margin-left: 24px;
      @include font(14, 400, 14);
    }
  }
}
</style>
