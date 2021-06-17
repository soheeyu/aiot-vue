<template>
  <article class="modal issue-modal">
    <header class="modal-header modal-header-color--white">
      <h1 class="modal__title">
        Issue list
      </h1>
      <button class="modal-header__close-button" @click="$emit('close')">
        <img src="@/assets/images/common/icon-close.png" alt="닫기">
      </button>
    </header>
    <div class="modal-content issue-modal-content">
      <div class="issue-summary">
        <button
          :class="['list-control__button list-control__button--critical', { 'is--active' : isCritical }]"
          @click="toggleCriticalControl">
          <mark class="list-control__number">{{criticalCnt}}</mark>
          <img class="list-control__icon" src="@/assets/images/common/icon-notice.png" alt="">심각
        </button>
        <button
          :class="['list-control__button list-control__button--warning', { 'is--active' : isWarning }]"
          @click="toggleWarningControl">
          <mark class="list-control__number">{{warningCnt}}</mark>
          <img class="list-control__icon" src="@/assets/images/common/icon-alert.png" alt="">경고
        </button>
        <button
          :class="['list-control__button list-control__button--info', { 'is--active' : isInfo }]"
          @click="toggleInfoControl">
          <mark class="list-control__number">{{infoCnt}}</mark>
          <img class="list-control__icon" src="@/assets/images/common/icon-info.png" alt="">정보
        </button>
      </div>
      <ul class="issue-list">
        <template v-for="(item, index) in data">
          <li class="list-item list-item--critical" v-if="item.machineStatus === '2' &&  isCritical" :key="index">
            <mark class="list-item__category list-item__date">{{item.created}}</mark>
            <mark class="list-item__category">{{item.machineCode}}</mark>
            {{item.content}}
          </li>
          <li class="list-item list-item--warning" v-if="item.machineStatus === '1' && isWarning" :key="index">
            <mark class="list-item__category list-item__date">{{item.created}}</mark>
            <mark class="list-item__category">{{item.machineCode}}</mark>
            {{item.content}}
          </li>
          <!-- <li class="list-item list-item--warning" v-if="isWarning">
            <mark class="list-item__category list-item__date">2020.11.27</mark>
            <mark class="list-item__category">[hm001]</mark>
            이슈내용
          </li> -->
          <li class="list-item list-item--info" v-if="item.machineStatus === '0' && isInfo" :key="index">
            <mark class="list-item__category list-item__date">{{item.created}}</mark>
            <mark class="list-item__category">{{item.machineCode}}</mark>
            {{item.content}}
          </li>
        </template>
      </ul>
    </div>
  </article>
</template>

<script>
export default {
  name: 'IssueListModal',
  data () {
    return {
      isCritical: true,
      isWarning: true,
      isInfo: true,
      criticalCnt: 0,
      warningCnt: 0,
      infoCnt: 0
    }
  },
  props: {
    data: {
      // type: Object
    }

  },
  methods: {
    // filterItems () {
    //   const filteredList = []
    //   // console.log('input item :', item)
    //   // console.log('this machineList ', this.machineList)
    //   for (var i in this.machineList) {
    //     if (this.machineList[i].machineType === item) {
    //       filteredList.push(this.machineList[i])
    //     }
    //   }
    //   // console.log('filteredItems : ', filteredList)
    //   return filteredList
    // },
    getCount () {
      this.criticalCnt = 0
      this.warningCnt = 0
      this.infoCnt = 0
      for (var i of this.data) {
        if (i.machineStatus === '2') {
          this.criticalCnt += 1
        } else if (i.machineStatus === '1') {
          this.warningCnt += 1
        } else if (i.machineStatus === '0') {
          this.infoCnt += 1
        }
      }
    },
    previewFiles (event) {
      console.log(event.target.files)
    },
    toggleCriticalControl () {
      this.isCritical = !this.isCritical
    },
    toggleWarningControl () {
      this.isWarning = !this.isWarning
    },
    toggleInfoControl () {
      this.isInfo = !this.isInfo
    }
  },
  mounted () {
    this.getCount()
  }
}
</script>

<style lang="scss">
@import "src/assets/style/components/modal";
@import "src/assets/style/components/list";
.issue-modal {
  overflow-y: auto;
  height: 60vh;
}
.issue-summary {
  background-color: #e6e6e6;
  padding: 20px;
}
.issue-modal {
  .list-control__button {
    text-align: center;
    &--warning {
      .list-control__icon {
        width: auto;
        margin-right: 15px;
      }
    }
  }
  .list-control__icon {
    margin-right: 6px;
    margin-left: -50px;
  }
}
.issue-list {
  padding: 40px 20px;
  .list-item {
    &__category {
      margin-right: 19px;
      &.list-item__date {
        margin-right: 13px;
      }
    }
  }
}
</style>
