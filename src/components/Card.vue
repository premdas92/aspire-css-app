<template>
  <div class="card-details-wrapper">
    <div class="my-cards">
      <div class="align-horizontally tabs-list">
        <div
          class="tab"
          v-for="tab in allTabs"
          :key="tab.id"
          @click="showCards(tab.id)"
          :class="activeTab === tab.id ? 'active' : ''"
        >
          {{ tab.text }}
        </div>
      </div>
      <div class="display-cards-block">
        <div class="show-card-number" v-if="activeTab === 1">
          <div class="align-horizontally inner">
            <span><img src="../assets/images/eye.svg" alt="eye" /></span>
            <span class="label">Show card number</span>
          </div>
        </div>
        <div class="debit-cards-wrapper" v-if="activeTab === 1">
          <div class="card">
            <div class="card-logo">
              <img src="../assets/images/Logo-white.svg" alt="logo" />
            </div>
            <div class="card-holder">Mark Henry</div>
            <div class="align-horizontally card-number">
              <div
                class="align-horizontally dots-wrapper"
                v-for="index in 4"
                :key="index"
              >
                <div class="dot" v-for="items in 4" :key="items"></div>
              </div>
              <span class="last-four-digit">2020</span>
            </div>
            <div class="align-horizontally details">
              <div class="detail-desc">
                <span>Thru: </span>
                <span>12/20</span>
              </div>
              <div class="align-horizontally detail-desc">
                <span>CVV: </span>
                <div class="align-horizontally stars">
                  <span>*</span>
                  <span>*</span>
                  <span>*</span>
                </div>
              </div>
            </div>
            <div class="visa">
              <div class="visa-logo">
                <img src="../assets/images/Visa Logo.svg" alt="visa" />
              </div>
            </div>
          </div>
        </div>
        <div class="company-cards-wrapper" v-if="activeTab === 2">
          Company Cards
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
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
.card-details-wrapper {
  padding: 0 24px 30px;
  @include desktopsmall {
    padding: 0;
  }
  .logo {
    width: 25px;
    float: right;
  }
  .my-cards {
    .tabs-list {
      justify-content: start;
      .tab {
        font-size: 13px;
        color: white;
        opacity: 0.5;
        cursor: pointer;
        @include desktopsmall {
          color: #000;
          opacity: 0.3;
        }
        &:nth-child(2) {
          margin-left: 33px;
        }
        &.active {
          padding-bottom: 5.5px;
          border-bottom: 2px solid $deep-sky;
          opacity: 1;
          font-weight: 800;
        }
      }
    }
    .display-cards-block {
      padding: 35px 0 25px 0;
      @include desktopsmall {
        padding-top: 60px;
      }
      .show-card-number {
        display: flex;
        justify-content: flex-end;
        .inner {
          width: 130px;
          background-color: white;
          padding: 5px 10px;
          border-top-left-radius: 6px;
          border-top-right-radius: 6px;
          @include desktopsmall{
            padding: 12px 10px;
          }
          .label {
            font-size: 12px;
            color: $green;
            font-weight: 800;
          }
        }
      }
      .debit-cards-wrapper {
        background-color: $green;
        padding: 24px;
        border-radius: 12px 0 12px 12px;
        @include desktopsmall {
          padding: 27px;
           border-radius: 12px;
        }
        .card {
          .card-logo {
            width: 75px;
            float: right;
            @include desktopsmall {
              width: 87px;
            }
          }
          .card-holder {
            font-size: 22px;
            color: white;
            padding-top: 30px;
            letter-spacing: 0.53px;
            font-weight: bold;
            @include desktopsmall {
              font-size: 24px;
            }
          }
          .card-number {
            padding-top: 30px;
            .dots-wrapper {
              width: 45px;
              .dot {
                height: 8px;
                width: 8px;
                background-color: white;
                border-radius: 50%;
                @include desktopsmall {
                  height: 9px;
                  width: 9px;
                }
              }
            }
            .last-four-digit {
              color: white;
              @include desktopsmall {
                letter-spacing: 5px;
              }
            }
          }
          .details {
            padding-top: 13px;
            color: white;
            width: 170px;
            @include desktopsmall {
              padding-top: 22px;
            }
            .detail-desc {
              .stars {
                span {
                  display: inline-block;
                  width: 15px;
                  height: 20px;
                  font-size: 20px;
                  text-align: center;
                }
              }
            }
          }
          .visa {
            display: flex;
            justify-content: flex-end;
            .visa-logo {
              width: 50px;
              @include desktopsmall {
                width: 66px;
              }
            }
          }
        }
      }
      .company-cards-wrapper {
        text-align: center;
        color: white;
        @include desktopsmall {
          color: #000;
        }
      }
    }
  }
}
</style>
