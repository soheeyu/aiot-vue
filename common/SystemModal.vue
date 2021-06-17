<template>
  <div class="system-modal" v-if="active">
    <div class="system-modal-content">
      <header class="system-modal-header">
        <h2 class="system-modal__title">알림</h2>
        <button class="modal-header__close-button" @click="cancelModal">
          <img src="@/assets/images/common/icon-close.png" alt="닫기">
        </button>
      </header>
      <p class="system-modal__description">{{ msg }}</p>
      <div class="system-modal-button-area">
        <button class="system-modal-button" @click="confirmModal">
          {{ okText }}
        </button>
        <template v-if="isChoice">
          <button class="system-modal-button system-modal-button--cancel" @click="cancelModal">
            {{ cancelText }}
          </button>
        </template>
      </div>
    </div>
    <div class="system-modal-bg" @click="cancelModal"></div>
  </div>
</template>

<script>
import eventBus from '../../utils/eventBus'
export default {
  name: 'SystemModal',
  data () {
    return {
      active: false,
      msg: '',
      okText: '확인',
      cancelText: '닫기',
      confirmHandler: null,
      isChoice: true
    }
  },
  props: {
    text: {
      type: String
    }
  },
  methods: {
    resetDialog () {
      this.active = false
      this.msg = ''
      this.okText = '확인'
      this.cancelText = '닫기'
      this.confirmHandler = null
      this.isChoice = true
    },
    modalContent (payload) {
      this.active = payload.active
      this.msg = payload.msg || this.msg
      this.confirmHandler = payload.confirmHandler || this.confirmHandler
      this.isChoice = !payload.isChoice ? payload.isChoice : this.isChoice
      this.okText = payload.okText || this.okText
      this.cancelText = payload.cancelText || this.cancelText
    },
    cancelModal () {
      if (this.confirmHandler && this.confirmHandler.cancel) {
        this.confirmHandler.cancel()
      }
      this.resetDialog()
      this.active = false
    },
    confirmModal () {
      if (this.confirmHandler && this.confirmHandler.ok) {
        this.confirmHandler.ok()
      }
      this.resetDialog()
      this.active = false
    }
  },
  beforeMount () {
    eventBus.$on('dialog', this.modalContent)
  },
  beforeDestroy () {
    eventBus.$off('dialog', this.modalContent)
  }
}
</script>

<style lang="scss" scoped>
.system-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  &-bg {
    position: absolute;
    left: 0;
    top: 0;
    display: block;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,.4)
  }
  &-header {
    background: #3c4b77;
    padding: 0.8rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  &__title {
    font-size: 1rem;
    color: $white;
  }
  &__description {
    font-size: 0.9rem;
    margin-top: 40px;
    margin-bottom: 40px;
  }
  &-content {
    width: 500px;
    border-radius: 10px;
    box-shadow: 0 4px 53px 15px rgba(72, 68, 66, 0.5);
    background-color: $white;
    position: relative;
    z-index: 1111;
    box-sizing: border-box;
    padding: 0 0 30px;
    text-align: center;
    overflow: hidden;
  }
  .system-modal-button {
    width: 140px;
    height: 60px;
    border-radius: 10px;
    background-color: #3c4a77;
    text-transform: uppercase;
    letter-spacing: -0.8px;
    color: $white;
    font-size: 0.9rem;
    &--cancel {
      margin-left: 20px;
      background-color: #e15b3d;
    }
  }
}
</style>
