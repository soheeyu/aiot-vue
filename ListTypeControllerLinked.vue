<template>
  <article ref="controller" :class="['controller', {'is--quater': line === 4, 'is--active': activeIndex === index }]" @click="showDetail(index)">
    <header class="controller-header">
      <img src="@/assets/images/common/icon-humidity.png" alt="" class="controller__icon">
      <div class="controller-header-info">
        <h2 class="controller__name">m01 - hm002</h2>
        <em v-if="controllerType === 'temperature'"  class="controller__category">온도 컨트롤러</em>
        <em v-else class="controller__category">습도 컨트롤러</em>
      </div>
      <mark class="controller__mark">70</mark>
    </header>
    <div class="controller-content">
      <p class="controller-content-content controller-content-content--subject">
        <strong class="controller-content-content__subject">Parameter</strong>
        <strong class="controller-content-content__subject">Value</strong>
      </p>
      <p class="controller-content-content controller-content-content--count">
        <span class="controller-content-content__subject">Count</span>
        <strong class="controller-content-content__value">74</strong>
      </p>
      <p class="controller-content-content  controller-content-content--temperature">
        <span class="controller-content-content__subject">Temperature</span>
        <strong class="controller-content-content__value">47</strong>
      </p>
    </div>
  </article>
</template>

<script>
import LinkedDetailInfoModal from '@/components/LinkedDetailInfoModal'
export default {
  name: 'ListTypeControllerLinked',
  props: {
    isShowDetail: {
      type: Boolean,
      default: false
    },
    controllerType: {
      type: String,
      default: 'temperature'
    },
    index: {
      type: Number
    },
    activeIndex: {
      type: null
    },
    data: {},
    line: {
      type: Number,
      default: 3
    }
  },
  methods: {
    goToControl () {},
    showDetail (index) {
      this.$modal.show(
        LinkedDetailInfoModal,
        {
          data: {}
        },
        {
          width: '1600',
          height: '90%'
        }
      )
      this.$emit('changeItem', index)
    }
  }
}
</script>

<style lang="scss" scoped>
  .controller {
    width: 31.1%;
    box-shadow: 0 4px 5.3px 1.8px rgba(72, 68, 66, 0.5);
    border: solid 1px rgba(255,255,255,.3);
    background-blend-mode: multiply;
    background-image: linear-gradient(to top, rgba(122, 144, 211, 0.3), rgba(215, 215, 215, 0.3));
    margin-left: 3.35%;
    box-sizing: border-box;
    border-radius: 10px;
    overflow: hidden;
    margin-top: 30px;
    opacity: 0.9;
    float: left;

    &.is--inactive {
      opacity: 0.3;
    }
    &.is--active {
      opacity: 1;
      box-shadow: 0 4px 5.3px 1.8px rgba(72, 68, 66, 0.1);
      //border: solid 1px rgba(255,255,255,1);
      //background-blend-mode: multiply;
      //background-image: linear-gradient(to top, rgba(122, 144, 211, 0.3), rgba(215, 215, 215, 0.3));
      .controller-header {
        background-color: rgba(7, 14, 35, 1);
      }
      .controller-header-info .controller__name {
        opacity: 1;
      }
    }
    &:nth-child(3n+1) {
      margin-left: 0;
    }
    &.is--quater {
      width: 22.4875%;
      &:nth-child(3n+1) {
        margin-left: 3.35%;
      }
      &:nth-child(4n+1) {
        margin-left: 0;
      }
    }
    &-header {
      display: flex;
      align-items: center;
      position: relative;
      padding: 22px 31px;
      background-color: rgba(7, 14, 35, 0.5);
      height: 113px;
      box-sizing: border-box;
      &-info {
        margin-left: 14px;
        margin-top: 4px;
        .controller {
          &__name {
            color: rgba(145, 206, 200, 0.4);
            font-size: 0.9rem;
            text-transform: uppercase;
            opacity: 0.4;
            margin-bottom: 10px;
            font-weight: normal;
          }
          &__category {
            color: $white;
            font-size: 1.16rem;
          }
        }
      }
    }
    &__mark {
      position: absolute;
      right: 0;
      top: 0;
      width: 51px;
      height: 51px;
      font-size: 0.8rem;
      text-align: right;
      padding-right: 9px;
      box-sizing: border-box;
      padding-top: 4px;
      letter-spacing: -0.5px;
      color: $white;
      background: url("../assets/images/common/rounded-rectangle.png") no-repeat 0 0;
    }
  }
  .controller-content {
    padding: 0 6px;
    &-content {
      color: $white;
      font-size: 0.9rem;
      display: flex;
      justify-content: space-between;
      box-sizing: border-box;
      align-items: center;
      height: 68px;
      padding: 0 25px;
      border-radius: 4px;
      position: relative;
      margin-bottom: 12px;
      &:after {
        content: '';
        width: calc(100% + 12px);
        height: 1px;
        display: block;
        background: rgba(255, 255, 255, 0.3);
        position: absolute;
        bottom: -7px;
        left: -6px;
      }
      &__subject {
        letter-spacing: -0.2px;
      }
      &--subject {
        height: 79px;
        padding: 11px 26px 0;
      }

      &--count {
        background-color: #d5955b;
      }
      &--temperature {
        background-color: #57ab6c;
        border-bottom: 0;
        margin-bottom: 6px;
        &:after {
          content: none;
        }
      }
      &__value {
        font-size: 1.08rem;
        font-weight: 800;
      }
    }
    position: relative;
    &:hover {
      .controller-content-hover {
        display: flex;
      }
    }
    &-hover {
      display: none;
      width: 100%;
      height: calc(100% + 119px);
      position: absolute;
      top: -113px;
      left: 0;
      background: rgba(0,0,0,.7);
      align-items: center;
      justify-content: center;
      flex-direction: column;
      .controller-content-hover {
        &__button {
          display: block;
          box-shadow: 0px 4px 2.7px 0.3px rgba(72, 68, 66, 0.5);
          width: 200px;
          height: 70px;
          color: $white;
          font-size: 1.16rem;
          border-radius: 10px;
          background-color: #8d8fa0;
          text-align: center;
          &:first-child {
            margin-bottom: 10px;
            background-color: #46c38a;
          }
        }
      }
    }
  }
</style>
