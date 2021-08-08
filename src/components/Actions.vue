<template>
  <div class="actions-wrapper">
    <div class="actions-inner-wrapper">
      <div class="align-horizontally actions-list">
        <div class="action" v-for="actions in allActions" :key="actions.id">
          <div class="icon">
            <img :src="actions.icon" :alt="actions.name" />
          </div>
          <div class="name">{{ actions.name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import FreezeCard from "../assets/images/Freeze card.svg";
import SpendLimit from "../assets/images/Set spend limit.svg";
import GPay from "../assets/images/GPay.svg";
import ReplaceCard from "../assets/images/Replace card.svg";
import DeactivateCard from "../assets/images/Deactivate card.svg";
export default {
  name: "Actions",
  data: function () {
    return {
      allActions: [
        {
          name: "Freeze card",
          icon: FreezeCard,
          id: 1,
        },
        {
          name: "Set spend limit",
          icon: SpendLimit,
          id: 2,
        },
        { name: "Add to GPay", icon: GPay, id: 3 },
        {
          name: "Replace card",
          icon: ReplaceCard,
          id: 4,
        },
        {
          name: "Cancel card",
          icon: DeactivateCard,
          id: 5,
        },
      ],
    };
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/app.scss";
.actions-wrapper {
  .actions-inner-wrapper {
    background-color: $light-sky;
    border-top-left-radius: 25px;
    border-top-right-radius: 25px;
    .actions-list {
      padding: 20px 27px;
      .action {
        .icon {
          padding-bottom: 7px;
          width: 32px;
          margin: 0 auto;
        }
        .name {
          text-align: center;
          font-size: 12px;
          color: $primary;
          @include desktopsmall{
            font-size: 13px;
          }
        }
      }
    }
  }
}
</style>