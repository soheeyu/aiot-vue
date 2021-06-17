<template>
  <div :is="headerTag" class="page-header">
    <component :is="tag" class="page-header__title">
      <slot name="title" />
    </component>
    <component :is="subTag" class="page-header__title--sub">
      <slot name="subTitle" />
    </component>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    tag: {
      type: String,
      default: 'h2'
    },
    subTag: {
      type: String,
      default: 'small'
    },
    headerTag: {
      type: String,
      default: 'header'
    }
  }
}
</script>

<style lang="scss" scoped>
.page-header {
  color: $white;
  display: flex;
  align-items: center;
  &__title {
    @include setText(1.166rem, normal, auto);
    letter-spacing: -0.5px;
  }
  &__title--sub {
    display: block;
    text-align: center;
    text-transform: uppercase;
    @include setText(0.93rem, 500, 1.5);
    letter-spacing: -0.5px;
    &:before {
      content: '';
      width: 1px;
      height: 35px;
      display: inline-block;
      background-color: $white;
      margin-right: 30px;
      margin-left: 30px;
      vertical-align: middle;
    }
  }
}
</style>
