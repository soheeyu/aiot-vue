<template>
  <article class="modal linked-facility-list-modal">
    <header class="modal-header modal-header-color--gradient">
      <h1 class="modal__title">
        연결된 설비목록 <small class="modal__title-sub">M01</small>
      </h1>
      <button class="modal-header__close-button" @click="$emit('close')">
        <img src="@/assets/images/common/icon-close.png" alt="닫기">
      </button>
    </header>
    <div class="linked-facility-list-content">
      <div class="facility-items">
        <list-type-controller-linked v-for="(item, index) in 6" :key="index" :line="4" :activeIndex="activeIndex" :index="index" @changeItem="onChangeItem"/>
      </div>
    </div>
  </article>
</template>

<script>
import ListTypeControllerLinked from '@/components/ListTypeControllerLinked'
export default {
  name: 'LinkedFacilityListModal',
  components: {
    ListTypeControllerLinked
  },
  data () {
    return {
      isShowModal: false,
      activeIndex: null
    }
  },
  props: {
    detail: {
      type: Object
    }
  },
  methods: {
    onChangeItem (payload) {
      this.activeIndex = payload
      this.isShowModal = true
    }
  }
}
</script>

<style lang="scss" scoped>
@import "src/assets/style/components/modal";
.facility-items {
  max-height: 79vh;
  padding: 0 30px 30px;
  box-sizing: border-box;
  overflow-y: auto;
  position: relative;
}
.linked-facility-content {
  max-height: 398px;
  overflow-y: auto;
}
.linked-facility-list-modal {
  background-repeat: no-repeat;
  background-image: url("../assets/images/linked-facility-bg.png");
  background-position: 50% 50%;
  background-size: cover;
  .linked-facility-list-content {
  }
}
</style>
