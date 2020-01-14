<template>
  <div class="nav">
    <div class="left">Charlie Liu</div>
    <div class="right">
      <div class="links">
        <a href>Dribbble</a>/
        <a href>Zcool</a>/
        <a href>Instagram</a>/
        <a href>Weibo</a>
      </div>
      <a href class="langSwitch">EN</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nav',
};
</script>

<style lang="scss" scoped>
@import '../style/global.scss';

.nav {
  width: 100vw;
  height: 100px;
  padding: 0 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;

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
      display: flex;
      justify-content: center;
      align-items: center;
      width: 36px;
      height: 36px;
      border: 1px solid #000000;
      margin-left: 24px;
    }
  }
}
</style>
