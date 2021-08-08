<template>
  <div class="balance-details-wrapper">
    <div class="mobile-only logo">
      <img src="../assets/images/Logo.svg" alt="logo" />
    </div>
    <div class="align-horizontally account-balance-wrapper">
      <div class="left">
        <div class="bal-label">Available balance</div>
        <div class="align-horizontally balance">
          <div class="dollars">$$</div>
          <div class="amount">3,000</div>
        </div>
      </div>
      <div class="right">
        <div class="align-horizontally new-card-wrapper">
          <div class="plus-icon">
            <img src="../assets/images/box.svg" alt="plus-icon" />
          </div>
          <div class="new-card">New card</div>
        </div>
        <div class="align-horizontally new-card-wrapper-mobile">
          <div class="plus-icon">
            <img src="../assets/images/box-white.svg" alt="plus-icon" />
          </div>
          <div class="new-card">New card</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Balance",
  data: function () {
    return {
      allTabs: [
        {
          text: "My debit cards",
          id: 1,
        },
        {
          text: "All company cards",
          id: 2,
        },
      ],
      activeTab: 1,
    };
  },
  methods: {
    showCards: function (id) {
      this.activeTab = id;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/app.scss";
.balance-details-wrapper {
  .logo {
    width: 25px;
    float: right;
  }
  .account-balance-wrapper {
    padding-bottom: 30px;
    align-items: flex-end;
    .left {
      color: white;
      @include desktopsmall {
        color: #000;
      }
      .balance {
        padding-top: 16px;
        width: 115px;
        .dollars {
          background: $green;
          border-radius: 4px;
          padding: 3px 13px;
          @include desktopsmall {
            color: white;
          }
        }
        .amount {
          font-size: 24px;
          font-weight: bold;
        }
      }
    }
    .right {
      .new-card-wrapper {
        width: 80px;
        cursor: pointer;
        @include desktopsmall {
          display: none;
        }
        .plus-icon {
          display: inline-flex;
        }
        .new-card {
          color: $deep-sky;
          font-size: 13px;
        }
      }
      .new-card-wrapper-mobile {
        display: none;
        @include desktopsmall {
          display: flex;
          width: 80px;
          cursor: pointer;
          background-color: $cool-blue;
          padding: 9px 12px;
          border-radius: 4px;
        }
        .plus-icon {
          display: inline-flex;
        }
        .new-card {
          color: white;
          font-size: 13px;
          font-weight: 500;
        }
      }
    }
  }
}
</style>