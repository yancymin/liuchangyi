<template>
  <div class="home">
    <Nav />
    <main>
      <div class="left">
        <div class="info">
          <h1>A relentless mind focused on crafting beautiful user experience</h1>
          <p>Currently located in Wuhan, CN as a designer of Geetest</p>
          <div class="contact">
            <a href>
              <img src="../assets/gmail.svg" alt /> Gmail
            </a>
            <a href>
              <img src="../assets/wechat.svg" alt />WeChat
            </a>
          </div>
        </div>
        <footer>© 2020 Charlie Liu All rights reserved</footer>
      </div>
      <img src="../assets/me.png" alt class="right" />
    </main>
  </div>
</template>

<script>
import Nav from '@/components/Nav.vue';

export default {
  name: 'home',
  components: {
    Nav,
  },
};
</script>

<style lang="scss" scoped>
@import '../style/global.scss';

.home {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;

  main {
    position: relative;
    display: flex;
    justify-content: space-between;
    max-width: 1200px;
    width: 100%;
    height: calc(100vh - 100px);

    .left {
      max-width: 600px;
      padding-top: 16%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;

      h1 {
        @include font(44, 400, 55);
        margin-bottom: 24px;
      }

      p {
        @include font(18, 400, 22);
      }

      .contact {
        display: flex;
        margin-top: 96px;

        a {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 144px;
          height: 48px;
          border: 1px solid #000000;
          cursor: pointer;
          transition: all 0.25s ease;

          &:hover {
            background: black;
            color: white;
            &:nth-of-type(2) {
              &::after {
                opacity: 1;
              }
            }
          }

          img {
            width: 24px;
            height: 24px;
            margin-right: 18px;
          }

          &:nth-of-type(1) {
            margin-right: 24px;
          }
          &:nth-of-type(2) {
            position: relative;
            &::after {
              opacity: 0;
              position: absolute;
              top: 54px;
              content: '';
              display: block;
              width: 144px;
              height: 144px;
              background: url('../assets/QR.png') no-repeat;
              background-size: cover;
              transition: all 0.25s ease;
            }
          }
        }
      }

      footer {
        @include font(14, 400, 14);
        opacity: 0.5;
        margin-bottom: 20px;
      }
    }

    .right {
      width: 100%;
      max-width: 700px;
      position: absolute;
      bottom: -2px;
      right: 0;
    }
  }
}
</style>
