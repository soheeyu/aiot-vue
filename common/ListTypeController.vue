<template>
  <article :class="['controller', {'is--quater': line === 4}, {'is--disable':data.machineCode === 'he02'}]">
    <header class="controller-header">
      <img v-if="controllerType === 'temperature'" src="@/assets/images/common/icon-temperature.png" alt="" class="controller__icon">
      <img v-else src="@/assets/images/common/icon-humidity.png" alt="" class="controller__icon">
      <div class="controller-header-info">
        <h2 class="controller__name">{{data.PmachineCode}} - {{data.machineCode}}</h2>
        <em v-if="controllerType === 'temperature'"  class="controller__category">{{data.machineType}}</em>
        <em v-else class="controller__category">습도 컨트롤러</em>
      </div>
      <mark class="controller__mark">70</mark>
    </header>
    <div :class="['controller-content', {'is--disable': index === 0}]" v-if="isShowValue">
      <p class="controller-content-content controller-content-content--subject">
        <strong class="controller-content-content__subject">Parameter</strong>
        <strong class="controller-content-content__subject">Value</strong>
      </p>
      <!-- <p class="controller-content-content controller-content-content--count">
        <span class="controller-content-content__subject">Count</span>
        <strong class="controller-content-content__value">74</strong>
      </p> -->
      <template v-for="(item, index) in recentDataset">
      <p class="controller-content-content controller-content-content--temperature" :key="index">
        <span class="controller-content-content__subject" :key="index">{{item.machineParam}}</span>
        <strong class="controller-content-content__value" :key="index">{{item.machineValue}}</strong>
      </p>
      </template>
      <template v-for="(stat, index) in recentStatset">
      <p class="controller-content-content controller-content-content--temperature" :key="index">
        <span class="controller-content-content__subject" :key="index">{{stat.machineStatus}}</span>
      </p>
      </template>
      <div class="controller-content-hover">
        <button class="controller-content-hover__button" @click="goToControl">Control</button>
        <button class="controller-content-hover__button" @click="showDetail">Detail</button>
      </div>
    </div>
  </article>
</template>

<script>
import DetailInfoAxios from '@/components/DetailInfoAxios'
export default {
  name: 'ListTypeController',
  props: {
    isShowValue: {
      type: Boolean,
      default: false
    },
    controllerType: {
      type: String,
      default: 'temperature'
    },
    data: {},
    line: {
      type: Number,
      default: 3
    },
    index: {
      type: Number
    }
  },
  data () {
    return {
      dataset: [],
      recentDataset: []
    }
  },
  methods: {
    getDataset () {
      const baseURL = 'http://118.67.130.122:18001'
      this.$http.get(`${baseURL}/machine/getdata/${this.data.machineCode}`)
        .then((result) => {
          console.log('dataset : ', result.data)
          this.dataset = result.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    getRecentData () {
      const baseURL = 'http://118.67.130.122:18001'
      this.$http.get(`${baseURL}/machine/getdata/${this.data.machineCode}/recent`)
        .then((result) => {
          console.log('recentDataset : ', result.data)
          this.recentDataset = result.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    goToControl () {
      window.open('https://www.naver.com', '_blank')
    },
    showDetail () {
      this.$modal.show(
        DetailInfoAxios,
        {
          data: {}
          // activeIndex: activeIndex
        },
        {
          width: '90%',
          height: '90%'
        }
      )
    }
  },
  mounted () {
    this.getDataset()
    this.getRecentData()
  }
}
</script>

<style lang="scss" scoped>
  .controller {
    width: 348px;
    box-shadow: 0 4px 5.3px 1.8px rgba(72, 68, 66, 0.5);
    border: solid 1px rgba(255,255,255,.3);
    background-blend-mode: multiply;
    background-image: linear-gradient(to top, rgba(122, 144, 211, 0), rgba(215, 215, 215, 0.3));
    box-sizing: border-box;
    border-radius: 10px;
    overflow: hidden;
    margin-top: 30px;
    float: left;
    margin-left: 20px;
    &.is--disable {
      // border: none;
       .controller-content-content:not(.controller-content-content--subject) {
        background-color: #7b849a;
      }
      .controller-header  {
        .controller__icon,
        .controller-header-info {
          opacity: .6;
        }
      }
      .controller-header {
        background-image: linear-gradient(to top, rgba(95, 95, 95, 0.6), rgba(95, 95, 95, 0.6));
      }
      .controller__name {
        color:#fff;
      }
    }

    //&:nth-child(3n+1) {
    //  margin-left: 0;
    //}
    // & + .controller {
    // }
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
      background: url("../../assets/images/common/rounded-rectangle.png") no-repeat 0 0;
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
    &:not(.is--disable):hover {
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
