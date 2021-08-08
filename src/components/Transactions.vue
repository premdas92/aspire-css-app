<template>
  <div class="workaround-wrapper">
    <div class="workaround-inner-wrapper">
      <div class="cards-wrapper">
        <div class="card" v-for="items in allCards" :key="items.id">
          <div class="card-inner-wrapper" @click="openAccordian(items.id)">
            <div class="align-horizontally inside-one">
              <div class="align-horizontally left">
                <div class="icn">
                  <img :src="items.icon" :alt="items.name" />
                </div>
                <div class="display-name">{{ items.name }}</div>
              </div>
              <div class="right">
                <div
                  class="chevron"
                  :class="activeAccordianIndex === items.id ? 'rotate' : ''"
                >
                  <img src="../assets/images/down-arrow.svg" alt="down-arrow" />
                </div>
              </div>
            </div>
          </div>

          <div
            class="card-inside-things"
            :class="activeAccordianIndex === items.id ? 'active' : ''"
          >
            <div
              class="align-horizontally inside-inner"
              v-for="(data, index) in items.cardTransactions"
              :key="index"
            >
              <div class="align-horizontally left-insider">
                <div class="transaction-icon">
                  <img :src="data.icon" :alt="data.name" />
                </div>
                <div class="description">
                  <div class="name">{{ data.name }}</div>
                  <div class="date">{{ data.date }}</div>
                  <div class="align-horizontally add-ons">
                    <div class="icn">
                      <img
                        src="../assets/images/business-and-finance.svg"
                        alt="ic"
                      />
                    </div>
                    <div class="others">{{ data.others }}</div>
                  </div>
                </div>
              </div>
              <div
                class="right-insider"
                :class="data.transactionType === 'credit' ? 'credit' : 'debit'"
              >
                <span>{{ data.transactionType === "credit" ? "+" : "-" }}</span>
                <span class="currency">$$</span>
                <span>{{ data.amount }}</span>
              </div>
            </div>
            <div class="all-transactions">View all card transactions</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import CardIcon from "../assets/images/card-icon.svg";
import TransactionIcon from "../assets/images/transactions.svg";
import FileStorage from "../assets/images/file-storage.svg";
import Flights from "../assets/images/flights.svg";
import MegaPhone from "../assets/images/megaphone.svg";
export default {
  name: "Transactions",
  data: function () {
    return {
      allCards: [
        {
          name: "Card details",
          icon: CardIcon,
          id: 1,
          cardTransactions: [
            {
              transactionType: "credit",
              icon: FileStorage,
              name: "Hamleys",
              date: "20 May 2020",
              amount: "150",
              others: "Refund on debit card",
            },
          ],
        },
        {
          name: "Recent transactions",
          icon: TransactionIcon,
          id: 2,
          cardTransactions: [
            {
              transactionType: "credit",
              icon: FileStorage,
              name: "Hamleys",
              date: "20 May 2020",
              amount: "150",
              others: "Refund on debit card",
            },
            {
              transactionType: "debit",
              icon: Flights,
              name: "Hamleys",
              date: "20 May 2020",
              amount: "150",
              others: "Charged to debit card",
            },
            {
              transactionType: "debit",
              icon: MegaPhone,
              name: "Hamleys",
              date: "20 May 2020",
              amount: "150",
              others: "Charged to debit card",
            },
          ],
        },
      ],
      activeAccordianIndex: 2,
    };
  },
  methods: {
    openAccordian: function (id) {
      this.activeAccordianIndex = id;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/app.scss";
.workaround-wrapper {
  padding: 24px;
  background-color: white;
  @include desktopsmall {
    width: 50%;
    padding-top: 115px;
    padding-left: 45px;
  }
  .workaround-inner-wrapper {
    .cards-wrapper {
      .card {
        margin-bottom: 24px;
        .card-inner-wrapper {
          background-color: #f5f9ff;
          border: 1px solid #f5f5f5;
          padding: 26px 24px;
          cursor: pointer;
        }
        .card-inside-things {
          padding: 0 24px;
          border: 1px solid #f5f5f5;
          display: none;
          .inside-inner {
            align-items: flex-start;
            padding: 24px 0;
            border-bottom: 1px solid #f5f5f5;
            .left-insider {
              .transaction-icon {
                display: grid;
                place-items: center;
                border-radius: 50%;
                background-color: #009dff1a;
                width: 48px;
                height: 48px;
                img {
                  width: 16px;
                }
              }
              .description {
                padding-left: 12px;
                .name {
                  padding-bottom: 4px;
                }
                .date {
                  color: #aaaaaa;
                  font-size: 13px;
                  padding-bottom: 18px;
                }
                .add-ons {
                  .icn {
                    background: $primary;
                    width: 24px;
                    height: 20px;
                    display: grid;
                    place-items: center;
                    border-radius: 50%;
                    img {
                      width: 10px;
                    }
                  }
                  .others {
                    font-size: 12px;
                    color: $cool-blue;
                    padding-left: 8px;
                  }
                }
              }
            }
            .right-insider {
              font-weight: 800;
              .currency{
                padding: 0 5px;
              }
              &.credit {
                color: $green;
              }
              &.debit {
                color: #000;
              }
            }
          }
          &.active {
            display: block !important;
          }
          .all-transactions {
            font-size: 13px;
            color: $green;
            font-weight: bold;
            background-color: #edfff5;
            border: 1px solid #edfff5;
            padding: 16px;
            text-align: center;
            margin-bottom: 30px;
          }
        }
        .inside-one {
          .left {
            .icn {
              width: 24px;
              height: 24px;
            }
            .display-name {
              color: $primary;
              font-weight: bold;
              padding-left: 12px;
            }
          }
          .right {
            .chevron {
              transition: all 0.3s ease-in-out;
              &.rotate {
                transform: rotate(180deg);
              }
            }
          }
        }
      }
    }
  }
}
</style>