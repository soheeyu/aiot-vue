<template>
  <header :class="['header', {'is--hide':!isShowHeader}]">
    <button class="header-arrow-button" @click="toggleHeader">
      <img v-if="!isShowHeader" src="@/assets/images/common/icon-right-arrow.png" alt="">
      <img v-else src="@/assets/images/common/icon-left-arrow.png" alt="">
    </button>
    <div class="header-info">
      <h1 class="header-info__logo"><img src="../assets/images/common/logo-sample.png" alt=""></h1>
      <strong class="header-info__name">홍길동</strong>
      <span class="header-info__info">현대<mark class="header-info__team">A team</mark></span>
    </div>
    <nav class="header-menu">
      <ul>
        <li class="header-menu__item">
          <router-link to="/CompanyList" class="header-menu-item__link">업체리스트</router-link>
        </li>
        <li class="header-menu__item">
          <router-link to="/FacilityList" class="header-menu-item__link">설비리스트</router-link>
        </li>
        <li class="header-menu__item">
          <router-link to="/ProductionStatus" class="header-menu-item__link">생산 현황</router-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderLeft',
  data () {
    return {
      isShowHeader: true
    }
  },
  methods: {
    toggleHeader () {
      this.$emit('toggleHeader')
      this.isShowHeader = !this.isShowHeader
    }
  }
}
</script>

<style scoped lang="scss">
  .header {
    position: fixed;
    top: 0;
    left: 0;
    width: 220px;
    height: 100%;
    background-color: rgba(255,255,255,0.15);
    color: $white;
    transition: left .4s ease-in;
    &.is--hide {
      left: - 220px;
    }
    &-arrow-button {
      position: absolute;
      top: 0;
      right: -40px;
      width: 40px;
      height: 40px;
      opacity: 0.3;
      background: rgba(255, 255, 255, 0.15);
      transition: all .4s ease-in;
      img {
        width: 24px;
      }
      &.is--hide {
        left: -40px;
      }
    }
    &-info {
      padding: 25px 10px 36px;
      text-align: center;
      border-bottom: 1px solid rgba(255,255,255,0.15);
      &__logo {
        img {
          overflow: hidden;
          border-radius: 50%;
          width: 100px;
          height: 100px;
        }
      }
      &__name {
        display: block;
        margin-top: 35px;
        margin-bottom: 7px;
      }
      &__info {
        color: #b1bcdc;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        font-size: 0.9rem;
      }
      &__team {
        color: #040404;
        font-size: 0.8rem;
        padding: 0 9px;
        background-color: rgba(255,255,255,0.4);
        margin-left: 6px;
      }
    }
    &-menu {
      &__item {
        border-bottom: 1px solid rgba(255,255,255,0.15);
        & + .header-menu__item {
          .header-menu-item__link {
            background-image: url("../assets/images/common/icon-menu-facility.png");
          }
          & + .header-menu__item {
            .header-menu-item__link {
              background-image: url("../assets/images/common/icon-menu-status.png");
            }
          }
        }
      }
      &-item__link {
        display: block;
        padding: 23px 35px 23px 80px;
        background-repeat: no-repeat;
        background-position: 34px 50%;
        background-image: url("../assets/images/common/icon-menu-list.png");
        font-size: 0.9rem;
        background-size: 26px;
        &:hover,
        &.router-link-active {
          background-color: #14343e;
        }
      }
    }
  }
</style>
