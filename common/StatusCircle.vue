<template>
  <div :class="['progress-pie-chart', {'is--large' : isLargeSize}]" ref="pieChart">
    <div class="pie-chart-progress">
      <div class="pie-chart-progress-fill" ref="pieChartFill"></div>
    </div>
    <div class="pie-chart-percents">
      <div class="pie-chart-text-area">
        <span>{{ percent }}%</span>
        <mark class="pie-chart-text__ratio" v-if="isLargeSize">1/4</mark>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StatusCircle',
  props: {
    percent: {
      type: Number
    },
    isLargeSize: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    init () {
      const deg = 360 * this.percent / 100
      if (this.percent > 50) {
        this.$refs.pieChart.classList.add('gt-50')
      }
      this.$refs.pieChartFill.style.transform = ('rotate(' + deg + 'deg)')
    }
  },
  mounted () {
    this.init()
  }
}
</script>

<style scoped lang="scss">
@mixin circle($size) {
  content: "";
  position: absolute;
  border-radius: 50%;
  left: calc(50% - #{$size/2});
  top: calc(50% - #{$size/2});
  width: $size;
  height: $size;
}

$size: 118px;
$largeSize: 204px;
.progress-pie-chart {
  width: $size;
  height: $size;
  border-radius: 50%;
  background-color: $white;
  position: relative;
  &.is--large {
    width: $largeSize;
    height: $largeSize;
    .pie-chart-progress {
      @include circle($largeSize);
      clip: rect(0, $largeSize, $largeSize, #{$largeSize/2});
      .pie-chart-progress-fill {
        @include circle($largeSize);
        clip: rect(0, #{$largeSize/2}, $largeSize, 0);
        background: #81CE97;
        transform: rotate(60deg);
      }
      .gt-50 & {
        clip: rect(0, #{$largeSize/2}, $largeSize, 0);
        .pie-chart-progress-fill {
          clip: rect(0, $largeSize, $largeSize, #{$largeSize/2});
          background: #E5E5E5;
        }
      }
    }
    .pie-chart-percents {
      @include circle(#{$largeSize/1.05});
      span {
        font-size: 1.41rem;
      }
    }
  }
  &.gt-50 {
    background-color: #81CE97;
  }
}
.pie-chart-progress {
  @include circle($size);
  clip: rect(0, $size, $size, #{$size/2});

  .pie-chart-progress-fill {
    @include circle($size);
    clip: rect(0, #{$size/2}, $size, 0);
    background: #81CE97;
    transform: rotate(60deg);
  }

  .gt-50 & {
    clip: rect(0, #{$size/2}, $size, 0);

    .pie-chart-progress-fill {
      clip: rect(0, $size, $size, #{$size/2});
      background: #E5E5E5;
    }
  }
}
.pie-chart-percents {
  @include circle(#{$size/1.1});
  background: $white;
  text-align: center;
  display: table;
  span {
    display: block;
    font-size: .83rem;
    font-weight: bold;
    color: #81CE97;
  }
}
.pie-chart-text-area {
  display: table-cell;
  vertical-align: middle;
}
.pie-chart-text__ratio {
  color: #dadada;
  font-size: 1.125rem;
  font-weight: bold;
  &:before {
    content: '';
    width: 128px;
    height: 1px;
    display: block;
    margin: 10px auto;
    background: #dadada;
  }
}
</style>
