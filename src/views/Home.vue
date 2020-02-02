<template>
  <div class="home" id="home" :class="{isDark: isDark}">
    <Nav @langBtn="langBtn" :isCN="isCN" />
    <main>
      <div class="left">
        <div class="info">
          <h1 :class="{enWidth: !isCN}" v-html="isCN?lang.CN[0]:lang.EN[0]"></h1>
          <p class="des" v-html="isCN?lang.CN[1]:lang.EN[1]"></p>
          <div class="contact">
            <a href="mailto:dcliuchangyi@gmail.com">
              <img src="../assets/gmail.svg" alt />
              {{isCN?lang.CN[2]:lang.EN[2]}}
            </a>
            <a @click="weChat()" v-clipboard:copy="this.copyText">
              <img src="../assets/wechat.svg" alt />
              <span class="weChat">{{isCN?lang.CN[3]:lang.EN[3]}}</span>
            </a>
          </div>
        </div>
        <footer>© 2020 Charlie Liu All rights reserved</footer>
      </div>
      <div class="right-pic">
        <footer>© 2020 Charlie Liu All rights reserved</footer>
        <img src="../assets/me.png" alt class="right" />
      </div>
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
  data() {
    return {
      count: 0,
      copyText: 'CHARLIE0105',
      isDark: true,
      isCN: true,
      copyedEN: 'Copyed',
      copyedCN: '已复制',
      lang: {
        CN: ['专注于创造美好的用户体验 而不懈努力', '目前位于中国武汉，任职 <a class="geetest" href="https://geetest.com">GeeTest</a> 的设计师。', '发邮件', '加微信'],
        EN: ['A relentless mind focused on crafting beautiful user experience', 'Currently located in Wuhan, CN as a designer of <a class="geetest" href="https://geetest.com">GeeTest</a>', 'Gmail', 'WeChat'],
      },
    };
  },
  updated() {
    this.gta();
    if (this.count !== 0) {
      this.weChat();
    }

    const weChat = document.querySelector('.weChat');

    if (this.isCN) {
      weChat.textContent = '加微信';
    } else {
      weChat.textContent = 'Wechat';
    }
  },
  mounted() {
    const gta = document.querySelector('.geetest');
    gta.style.color = '#347eff';

    this.gta();
    // const nowTime = new Date();

    // if (nowTime.getHours() >= 19 || nowTime.getHours() <= 7) {
    //   this.isDark = true;
    // } else {
    //   this.isDark = false;
    // }
    // const des = document.querySelector('.des');
    // des.addEventListener('mouseenter', () => {
    //   document.querySelector('.geetest').style.color = '#347eff';
    // });
    // des.addEventListener('mouseleave', () => {
    //   // document.querySelector('.geetest').style.color = '#ffffff';
    // });
  },

  methods: {
    weChat() {
      this.count += 1;
      const weChat = document.querySelector('.weChat');
      if (this.isCN) {
        weChat.textContent = this.copyedCN;
      } else {
        weChat.textContent = this.copyedEN;
      }

      setTimeout(() => {
        if (this.isCN) {
          weChat.textContent = '加微信';
        } else {
          weChat.textContent = 'Wechat';
        }
      }, 2000);
    },
    gta() {
      const gta = document.querySelector('.geetest');
      gta.style.color = '#347eff';
      gta.addEventListener('mouseenter', () => {
        gta.style.textDecoration = 'underline';
        gta.style.color = '#347eff';
      });
      gta.addEventListener('mouseleave', () => {
        gta.style.textDecoration = 'none';
        // gta.style.color = '#ffffff';
      });
    },
    langBtn() {
      this.isCN = !this.isCN;
    },
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
    max-width: 1160px;
    width: 100%;
    height: calc(100vh - 100px);

    .left {
      z-index: 99;
      max-width: 580px;
      padding-bottom: 100px;
      display: flex;
      flex-direction: column;
      justify-content: space-around;

      footer {
        position: absolute;
        bottom: 0;
      }

      h1 {
        @include font(44, 400, 55);
        margin-bottom: 24px;
      }

      p {
        @include font(18, 400, 22);
      }

      .contact {
        display: flex;
        margin-top: 10vh;

        a {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 144px;
          height: 48px;
          border: 1px solid #000000;
          cursor: pointer;
          transition: all 0.25s ease;
          @include font(14, 400, 14);
          color: white;

          &:hover {
            background: white;
            color: #070707;

            &:nth-of-type(2) {
              &::after {
                visibility: visible;
              }
            }
          }

          &:active {
            text-decoration: underline;
          }

          &:active {
            background: #070707;
            color: white;
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
              z-index: 999;
              visibility: hidden;
              position: absolute;
              top: 54px;
              content: '';
              display: block;
              width: 144px;
              height: 144px;
              background: url('../assets/QR.jpg') no-repeat;
              background-size: cover;
              transition: all 0.25s ease;
            }
          }
        }
      }
    }

    .right {
      z-index: 0;
      width: 100%;
      max-width: 600px;
      position: absolute;
      right: 0;
      top: 0;
      pointer-events: none;
    }
  }

  .right-pic footer {
    display: none;
  }
}
footer {
  @include font(14, 400, 14);
  opacity: 0.5;
  margin-bottom: 20px;
}

@media screen and (max-width: 980px) {
  #home {
    .nav {
      align-items: flex-start;
      flex-direction: column;
      padding: 32px 20px;

      ::v-deep .right {
        .links {
          margin-top: 28px;
          a {
            &:nth-of-type(1) {
              margin-left: 0;
            }
          }
        }
      }
      ::v-deep .langSwitch {
        position: absolute;
        top: 28px;
        right: 20px;
      }
    }

    h1 {
      max-width: 300px;
      @include font(24, 400, 30);
    }
    p {
      max-width: unset;
      @include font(14, 400, 17);
    }

    main {
      padding: 0 20px;
      flex-direction: column;
      height: unset;

      .left {
        max-width: unset;
        padding: 64px 0 20px 0;
        .contact {
          margin-top: 48px;

          a {
            width: 100%;

            &:nth-of-type(1) {
              margin-right: 12px;
            }

            &:nth-of-type(2) {
              &:hover {
                &::after {
                  display: none;
                }
              }
            }
          }
        }
        footer {
          display: none;
        }
      }

      .right-pic {
        position: relative;
        display: flex;
        justify-content: center;
        overflow: hidden;
        height: 480px;

        footer {
          position: absolute;
          bottom: 16px;
          display: block;
          z-index: 99;
          font-size: 10px;
          margin-bottom: 0;
        }
      }

      .right {
        // margin-top: 32px;
        pointer-events: none;
        right: 0;
      }
    }
  }
  // footer {
  //   z-index: 99;
  //   position: absolute;
  //   bottom: 20px;
  //   align-self: center;
  //   color: white;
  //   font-size: 12px;
  //   margin-bottom: 16px;
  // }
}

.isDark {
  background-color: #070707;

  h1,
  p,
  footer {
    color: white !important;
  }

  ::v-deep .nav {
    a,
    h1,
    div {
      color: white !important;
    }

    a {
      border-color: white !important;
    }
  }

  a {
    border-color: white !important;
    color: white;
  }
}
.enWidth {
  max-width: unset !important;
}
</style>
