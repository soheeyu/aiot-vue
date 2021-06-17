<template>
  <article class="company-add-modal modal">
    <header class="company-modal-header modal-header modal-header-color--white">
      <h1 v-if="isAdd" class="company-modal__title">
        회사를 등록하세요.
      </h1>
      <div v-else class="company-modal-header-data">
        <div class="company-modal-img">
          <img src="@/assets/images/common/logo-sample.png" alt="" class="company-modal__img">
<!--          <img :src="detail.src" alt="" class="company-modal__img">-->
        </div>
        <strong class="company-modal__name">{{ detail.companyName }}</strong>
      </div>
      <button class="modal-header__close-button" @click="$emit('close')">
        <img src="@/assets/images/common/icon-close.png" alt="닫기">
      </button>
    </header>
    <div class="company-modal-form-area">
      <form @submit.prevent="onSend" class="company-modal-form">
        <div class="company-modal-form-part" v-if="isAdd">
          <label for="companyName" class="company-modal__label">
            <img src="@/assets/images/common/icon-company.png" alt="">
          </label>
          <input v-model="detail.companyName" type="text" class="company-modal__input" id="companyName">
        </div>
        <div class="company-modal-form-part" v-if="isAdd">
          <label for="file" class="company-modal__label">
            <img src="@/assets/images/common/icon-photo.png" alt="">
          </label>
          <input @change="previewFiles" type="file" class="is--file company-modal__input" id="file">
        </div>
        <div class="company-modal-form-part">
          <label for="code" class="company-modal__label">
            <img src="@/assets/images/common/code.png" alt="">
          </label>
          <input v-model="detail.code" type="text" class="company-modal__input" id="code">
        </div>
        <div class="company-modal-form-part">
          <label for="website" class="company-modal__label">
            <img src="@/assets/images/common/icon-web.png" alt="">
          </label>
          <input v-model="detail.website" type="text" class="company-modal__input" id="website">
        </div>
        <div class="company-modal-form-part">
          <label for="name" class="company-modal__label">
            <img src="@/assets/images/common/icon-user.png" alt="">
          </label>
          <input v-model="detail.name"  type="text" class="company-modal__input" id="name">
        </div>
        <div class="company-modal-form-part">
          <label for="phone" class="company-modal__label">
            <img src="@/assets/images/common/icon-phone.png" alt="">
          </label>
          <input v-model="detail.phone" type="text" class="company-modal__input" id="phone">
        </div>
        <div class="company-modal-form-part">
          <label for="email" class="company-modal__label">
            <img src="@/assets/images/common/icon-email.png" alt="">
          </label>
          <input v-model="detail.email" type="text" class="company-modal__input" id="email">
        </div>
        <div class="company-modal-form-part">
          <label for="address" class="company-modal__label">
            <img src="@/assets/images/common/icon-location.png" alt="">
          </label>
          <input v-model="detail.address" type="text" class="company-modal__input" id="address">
        </div>
        <div class="company-modal-form-part">
          <label for="geo" class="company-modal__label">
            <img src="@/assets/images/common/geo.png" alt="">
          </label>
          <input v-model="detail.geo" type="text" class="company-modal__input" id="geo">
        </div>
        <div class="company-modal-button-area">
          <button class="company-modal-button" @click="onSend">SUBMIT</button>
          <button class="company-modal-button company-modal-button--clear" @click="clear">CLEAR</button>
        </div>
      </form>
    </div>
  </article>
</template>

<script>
export default {
  name: 'CompanyAddModal',
  props: {
    detail: {
      type: Object
    },
    isAdd: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    onSend () {
      this.$emit('close')
    },
    clear () {
      this.$emit('close')
    },
    previewFiles (event) {
      console.log(event.target.files)
    }
  }
}
</script>

<style lang="scss" scoped>
@import "src/assets/style/components/modal";
.company-modal {
  &-header {
    padding: 13px 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    &-data {
      display: flex;
      align-items: center;
    }
  }
  &__title {
    margin: .5rem 0.8rem;
    @include setText(0.9rem, 600)
  }
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
  &-form {
    &-area {
      padding: 0 20px 20px;
    }
    &-part {
      border-bottom: 1px solid #b6bed6;
      display: flex;
      padding: 15px 10px;
    }
  }
  &__label {
    width: 55px;
    //@include blind
    display: flex;
    align-items: center;
  }
  &__input {
    border: 0;
    width: 100%;
    height: 40px;
    padding-left: 10px;
    box-sizing: border-box;
    font-size: 0.9rem;
    &.is--file {
      //padding-top: 8px;
      border: 0;
      line-height: 40px;
      padding-left: 0;
      &::-ms-value {
        border: 0;
        padding-top: 0;
      }
    }
  }
  &-button {
    &-area {
      text-align: center;
      margin-top: 20px;
    }
    width: 140px;
    height: 60px;
    border-radius: 10px;
    background-color: #3c4a77;
    text-transform: uppercase;
    letter-spacing: -0.8px;
    color: $white;
    font-size: 0.9rem;
    &--clear {
      margin-left: 20px;
      background-color: #e15b3d;
    }
  }
}
</style>
