<template>
  <aside :class="['machine-list', {'is--close' : !isShowMachineList}]">
    <button class="machine-list-arrow-button" @click="toggleMachineList">
      <img v-if="isShowMachineList" src="@/assets/images/common/icon-right-arrow.png" alt="">
      <img v-else src="@/assets/images/common/icon-left-arrow.png" alt="">
    </button>
    <h1 class="machine-list__title">Machine list</h1>
    <div class="list-control">
      <button
        :class="['list-control__button list-control__button--running', { 'is--active' : isRunning }]"
        @click="toggleRunningControl">
        <mark class="list-control__number">7</mark>
        <img class="list-control__icon" src="@/assets/images/common/icon-running.png" alt="">가동
      </button>
      <button
        :class="['list-control__button', { 'is--active' : isNon }]"
        @click="toggleNonControl">
        <mark class="list-control__number">4</mark>
        <img class="list-control__icon" src="@/assets/images/common/icon-notice.png" alt="">비가동
      </button>
    </div>
    <ul class="list-control-result-list">
      <li class="list-item list-item--running" v-if="isRunning">
        <mark class="list-item__category">[hm001]</mark>
        해당항목들
      </li>
      <li class="list-item list-item--running"  v-if="isRunning">
        <mark class="list-item__category">[hm001]</mark>
        해당항목들
      </li>
      <li class="list-item" v-if="isNon">
        <mark class="list-item__category">[hm001]</mark>
        해당항목들
      </li>
    </ul>
  </aside>
</template>

<script>
export default {
  name: 'MachineList',
  data () {
    return {
      isRunning: true,
      isNon: true
    }
  },
  props: {
    isShowMachineList: {
      type: Boolean
    }
  },
  methods: {
    toggleRunningControl () {
      this.isRunning = !this.isRunning
    },
    toggleNonControl () {
      this.isNon = !this.isNon
    },
    toggleMachineList () {
      this.$emit('toggleMachineList')
    }
  }
}
</script>

<style lang="scss" scoped>
@import "src/assets/style/components/list";
.machine-list-arrow-button {
  position: absolute;
  top: -40px;
  left: 0;
  width: 40px;
  height: 40px;
  opacity: 0.3;
  border: solid 1px #fff;
  //border-bottom: 0;
  transition: all .4s ease-in;
  img {
    width: 24px;
  }
}
  .machine-list {
    position: fixed;
    right: 0;
    width: 375px;
    top: 154px;
    height: 1383px;
    box-sizing: border-box;
    padding: 1px 0 327px;
    border-top-left-radius: 10px;
    box-shadow: 0 4px 5.3px 1.8px rgba(72, 68, 66, 0.5);
    border: solid 1px rgba(255,255,255,.03);
    background-blend-mode: multiply;
    background-image: linear-gradient(to top, rgba(122, 144, 211, 0.3), rgba(215, 215, 215, 0.3));
    transition: right .4s ease-in;
    &.is--close {
      right: - 375px;
      .machine-list-arrow-button {
        left: - 40px;
      }
    }
    &__title {
      font-size: 1.16rem;
      padding: 1.2rem;
      color: $white;
      font-weight: normal;
      background-color: #1e183c;
      overflow: hidden;
      border-top-left-radius: 10px;
    }

    .list-control-result {
      &-list {
        padding: 40px 20px;
        height: 62vh;
        overflow-y: auto;
        box-sizing: border-box;
      }
      //&__item {
      //  color: $white;
      //  height: 50px;
      //  padding: 0 12px;
      //  border-radius: 4px;
      //  box-sizing: border-box;
      //  display: flex;
      //  align-items: center;
      //  background-color: #949595;
      //  font-weight: bold;
      //  .result__category {
      //    font-size: 0.75rem;
      //    margin-right: 29px;
      //    text-transform: uppercase;
      //    color: #e6e6e6;
      //  }
      //  & + .list-control-result__item {
      //    margin-top: 20px;
      //  }
      //  &-running {
      //    background-color: #46c38a;
      //    .result__category {
      //      color: #c0ffe4;
      //    }
      //  }
      //}
    }
  }
</style>
