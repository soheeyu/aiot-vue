<template>
  <article class="list-item-card">
    <header class="list-item-card-header">
      <div class="list-item-card-profile">
        <div class="list-item-card-profile-img">
          <img src="@/assets/images/common/logo-sample.png" alt="" class="list-item-card-profile__img">
        </div>
        <div class="list-item-card-profile__name">corp03</div>
      </div>
      <div class="list-item-card-setting">
        <button class="list-item-card__button" @click="onEdit">
          <img src="@/assets/images/common/icon-setting.png" alt="설정">
        </button>
        <button class="list-item-card__button" @click="onRemove">
          <img src="@/assets/images/common/icon-trash.png" alt="삭제">
        </button>
      </div>
    </header>
    <div class="list-item-card-content">
      <div class="list-item-card-status-area">
        <div class="list-item-card-status">
          <strong class="item-status__subject">가동 현황</strong>
          <div class="status-graph">
            <div class="status-graph-donut">
              <status-circle :percent="10"/>
            </div>
          </div>
        </div>
        <div class="list-item-card-status">
          <strong class="item-status__subject">이슈 현황</strong>
          <strong class="item-status__issue">4</strong>
        </div>
      </div>
      <p class="list-item-card-info__item list-item-card-info__item-name">홍길동</p>
      <p class="list-item-card-info__item list-item-card-info__item-phone">010-1234-5678</p>
      <p class="list-item-card-info__item list-item-card-info__item-email">abcdef@naver.com</p>
      <p class="list-item-card-info__item list-item-card-info__item-address">서울특별시 금강산 123호</p>
    </div>
  </article>
</template>

<script>
import StatusCircle from '@/components/common/StatusCircle'
export default {
  name: 'ListTypeCard',
  components: {
    StatusCircle
  },
  props: {
    list: {
      type: Array
    }
  },
  methods: {
    onEdit () {
      this.$emit('onEditItem')
    },
    onRemove () {
      this.$emit('onRemoveItem')
    }
  }
}
</script>

<style scoped lang="scss">
.list-item-card {
  width: 30.82%;
  overflow: hidden;
  border-radius: 10px;
  color: $white;
  box-shadow: 0px 4px 5.3px 1.8px rgba(72, 68, 66, 0.5);
  border: solid 1px rgba(255,255,255,.3);
  background-blend-mode: multiply;
  background-image: linear-gradient(to top, rgba(122, 144, 211, 0.3), rgba(215, 215, 215, 0.3));
  margin-left: 3.77%;
  box-sizing: border-box;
  margin-bottom: 50px;
  &:nth-child(3n+1) {
    margin-left: 0;
  }
  &-header {
    background-color: rgba(7, 14, 35, 0.8);
    padding: 12px 19px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  &-profile {
    display: flex;
    align-items: center;
    &__img {
      width: 76px;
      height: 76px;
      border-radius: 50%;
    }
    &__name {
      text-transform: uppercase;
      margin-left: 22px;
      @include textClamp(1)
    }
  }
  &__button {
    margin: 0 8px;
  }
  &-content {
    //background: rgba(255,255,255,0.1);
    font-size: 0.9rem;
  }
  &-status {
    width: 100%;
    padding: 20px 20px 0;
    box-sizing: border-box;
    border-bottom: 1px solid $orange;
    font-size: 1rem;
    .item-status {
      &__subject {
        display: block;
        font-weight: normal;
      }
      &__issue {
        color: $orange;
        font-size: 7rem;
        display: block;
        text-align: right;
        line-height: 1;
        margin-top: 1.6rem;
      }
    }
    &:first-child {
      border-right: 1px solid rgba(215,215,215,.2);
      border-bottom: 1px solid $green;
    }
    &-area {
      display: flex;
    }
    .status-graph {
      &-donut {
        position: relative;
        margin: 1rem auto 0;
        width: 118px;
        height: 118px;
        border-radius: 50%;
        background: linear-gradient($green 63.34%, transparent 63.34%) 0 0;
        background-size: 50% 50%;
        transition: 1s;
      }
    }
  }
  &-info__item {
    border-bottom: 1px solid rgba(215,215,215,0.3);
    padding: 27px 30px 26px 97px;
    background-repeat: no-repeat;
    background-position: 25px 50%;
    font-size: 0.95rem;
    background-size: 23px;
    &-name {
      background-image: url("../../assets/images/common/icon-user.png");
    }
    &-phone {
      background-image: url("../../assets/images/common/icon-phone.png");
    }
    &-email {
      background-image: url("../../assets/images/common/icon-email.png");
    }
    &-address {
      background-image: url("../../assets/images/common/icon-location.png");
    }
    &:last-of-type {
      border-bottom: 0;
    }
  }
}
</style>
