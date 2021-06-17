<template>
  <div class="system-modal">
    <div class="system-modal-content">
      <h2 class="system-modal__title">알림</h2>
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
  </div>
</template>

<script>
export default {
  name: 'AlertModal',
  data () {
    return {
    }
  },
  props: {
    msg: {
      type: String
    },
    isChoice: {
      type: Boolean,
      default: false
    }
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
  &:after {
    position: absolute;
    left: 0;
    top: 0;
    content: '';
    display: block;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,.4)
  }
  &__title {
    background: #3c4b77;
    font-size: 1rem;
    color: $white;
    padding: 0.8rem;
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
