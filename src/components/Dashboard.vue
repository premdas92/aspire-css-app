<template>
  <div class="dashboard-wrapper">
    <div class="dashboard-inner">
      <div class="top">
        <Balance />
      </div>
      <div class="layout-wrapper">
        <div class="bottom">
          <Card />
          <Actions />
        </div>
        <Transactions />
      </div>
    </div>
  </div>
</template>
<script>
import Balance from "./Balance.vue";
import Card from "./Card.vue";
import Actions from "./Actions.vue";
import Transactions from "./Transactions.vue";
export default {
  name: "Dashboard",
  components: {
    Balance,
    Card,
    Actions,
    Transactions,
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/app.scss";
.dashboard-wrapper {
  background-color: $primary;
  @include desktopsmall {
    width: 80%;
    background-color: white;
  }
  .dashboard-inner {
    .top {
      padding: 30px 24px 0;
      @include desktopsmall {
        padding: 60px 0 0 60px;
      }
    }
    .layout-wrapper {
      @include desktopsmall {
        display: flex;
        padding: 0 0 0 60px;
      }
      .bottom {
        @include desktopsmall{
          width: 40%;
        }
      }
    }
  }
}
</style>