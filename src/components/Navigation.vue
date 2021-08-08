<template>
  <header>
    <div class="header-wrapper">
      <div class="align-horizontally links-wrapper">
        <div class="link" v-for="items in links" :key="items.id">
          <div class="icon">
            <img :src="items.icon" :alt="items.name" />
          </div>
          <div class="name">{{ items.name }}</div>
        </div>
      </div>
      <div class="desktop-navigation">
        <div class="logo">
          <img src="../assets/images/Aspire Logo.svg" alt="logo" />
        </div>
        <div class="slogan">
          Trusted way of banking for 3,000+ SMEs and startups in Singapore
        </div>
        <div class="desktop-links-wrapper">
          <div class="link" v-for="items in links" :key="items.id">
            <div class="icon">
              <img :src="items.icon" :alt="items.name" />
            </div>
            <div class="name">{{ items.name }}</div>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>
<script>
import Home from "../assets/images/Logo-gray.svg";
import Card from "../assets/images/Card.svg";
import Payments from "../assets/images/Payments.svg";
import Credit from "../assets/images/Credit-gray.svg";
import Account from "../assets/images/Account-gray.svg";
export default {
  name: "Navigation",
  data: function () {
    return {
      links: [
        { name: "Home", icon: Home, id: 1 },
        { name: "Cards", icon: Card, id: 2 },
        { name: "Payments", icon: Payments, id: 3 },
        { name: "Credit", icon: Credit, id: 4 },
        { name: "Settings", icon: Account, id: 5 },
      ],
    };
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/app.scss";
header {
  position: fixed;
  left: 0;
  right: 0;
  width: 100%;
  bottom: 0;
  z-index: 999;
  background: white;
  @include desktopsmall {
    position: static;
    width: 25%;
  }
  .header-wrapper {
    padding: 9px 30px;
    @include desktopsmall {
      padding: 0;
    }
    .links-wrapper {
      @include desktopsmall {
        display: none;
      }
      .link {
        .icon {
          height: 24px;
          width: 24px;
          margin: 0 auto;
          padding-bottom: 3px;
        }
        .name {
          font-size: 9px;
          color: $gray;
          text-align: center;
        }
        &:nth-child(2) {
          .name {
            color: $green;
          }
        }
      }
    }
    .desktop-navigation {
      display: none;
      @include desktopsmall {
        display: block;
        background-color: $primary;
        padding: 60px 48px 48px;
      }
      .logo {
        width: 125px;
      }
      .slogan {
        font-size: 15px;
        opacity: 0.3;
        color: white;
        padding-top: 19px;
        padding-bottom: 80px;
      }
      .desktop-links-wrapper {
        @include desktopsmall {
          height: 500px;
          display: flex;
          flex-direction: column;
          justify-content: space-between;
        }
        .link {
          .icon {
            height: 24px;
            width: 24px;
            float: left;
          }
          .name {
            font-size: 16px;
            color: white;
            text-align: center;
            float: left;
            padding-left: 16px;
          }
          &:nth-child(2) {
            .name {
              color: $green;
            }
          }
        }
      }
    }
  }
}
</style>