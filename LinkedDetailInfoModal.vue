<template>
  <article class="modal linked-detail-info-modal">
    <header class="modal-header modal-header-color--gradient">
      <h1 class="modal__title">
        Detail information
      </h1>
      <button class="modal-header__close-button" @click="$emit('close')">
        <img src="@/assets/images/common/icon-close.png" alt="닫기">
      </button>
    </header>
    <div class="modal-content info-modal-content">
      <div class="info-modal-content-top">
        <article class="info-modal-content-content info-modal-content-info">
          <h2 class="info-modal__title">Information</h2>
          <div class="info-modal-info">
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">ID</b>
              <strong class="info-modal-info__content">2</strong>
            </p>
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">pmched</b>
              <strong class="info-modal-info__content">Mo2</strong>
            </p>
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">pmchty</b>
              <strong class="info-modal-info__content">2</strong>
            </p>
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">cmched</b>
              <strong class="info-modal-info__content">HM003</strong>
            </p>
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">ipaddress</b>
              <strong class="info-modal-info__content">온도 컨트롤러</strong>
            </p>
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">created</b>
              <strong class="info-modal-info__content">2020-08.20T06.36.47.320000Z</strong>
            </p>
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">modified</b>
              <strong class="info-modal-info__content">Mo2</strong>
            </p>
            <p class="info-modal-info-part">
              <b class="info-modal-info__subject">status</b>
              <strong class="info-modal-info__content">0</strong>
            </p>
          </div>
        </article>
        <article class="info-modal-content-content info-modal-content-graph">
          <h2 class="info-modal__title">Graph
          <span class="chart__label">
            <b class="chart__label-box humidty">humidty</b>
            <b class="chart__label-box count">count</b>
          </span>
          </h2>
          <div class="info-modal-info info-modal-info-chart">
            <line-chart :chartData="chartData" :options="options"/>
          </div>
        </article>
      </div>
      <article class="info-modal-content-content info-modal-content-table info-modal-content-table--data">
        <h2 class="info-modal__title">Data table</h2>
        <div class="info-modal-table-area">
          <table class="info-modal-table info-modal-table--data">
            <thead>
              <tr>
                <th>Machine</th>
                <th>Submachine</th>
                <th>Type</th>
                <th>Parametter</th>
                <th>Value</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>M01</td>
                <td>HM003</td>
                <td>HC</td>
                <td>Count</td>
                <td>72</td>
              </tr>
              <tr>
                <td>M01</td>
                <td>HM003</td>
                <td>HC</td>
                <td>Count</td>
                <td>72</td>
              </tr>
              <tr>
                <td>M01</td>
                <td>HM003</td>
                <td>HC</td>
                <td>Count</td>
                <td>72</td>
              </tr>
            </tbody>
          </table>
          <div class="info-modal-table-pagination info-modal-table-pagination--data">
            <button class="pagination-button pagination-button-prev">
              <img src="@/assets/images/pagination-prev-white.png" alt="이전">
            </button>
            <div class="pagination-number-box">
              <input type="number" v-model="currentPage" class="pagination__input">
              <mark class="pagination__total-number">/ 27</mark>
            </div>
            <button class="pagination-button pagination-button-next">
              <img src="@/assets/images/pagination-next-white.png" alt="다음">
            </button>
          </div>
        </div>
      </article>
      <article class="info-modal-content-content info-modal-content-table info-modal-content-table--error">
        <h2 class="info-modal__title">Error table</h2>
        <div class="info-modal-table-area">
          <table class="info-modal-table">
            <thead>
            <tr>
              <th>Machine</th>
              <th>Submachine</th>
              <th>Type</th>
              <th>Code</th>
              <th>Status</th>
              <th>Content</th>
              <th>Created time</th>
              <th>Updated time</th>
            </tr>
            </thead>
            <tbody>
            <tr>
              <td>M01</td>
              <td>HM003</td>
              <td></td>
              <td>101</td>
              <td>0</td>
              <td>error occurrence</td>
              <td>2020-09-09t18:31:23/276666Z</td>
              <td>2020-09-09t18:31:23/276666Z</td>
            </tr>
            <tr>
              <td>M01</td>
              <td>HM003</td>
              <td></td>
              <td>101</td>
              <td>0</td>
              <td>error occurrence</td>
              <td>2020-09-09t18:31:23/276666Z</td>
              <td>2020-09-09t18:31:23/276666Z</td>
            </tr>
            <tr>
              <td>M01</td>
              <td>HM003</td>
              <td></td>
              <td>101</td>
              <td>0</td>
              <td>error occurrence</td>
              <td>2020-09-09t18:31:23/276666Z</td>
              <td>2020-09-09t18:31:23/276666Z</td>
            </tr>
            </tbody>
          </table>
          <div class="info-modal-table-pagination">
            <button class="pagination-button pagination-button-prev">
              <img src="@/assets/images/pagination-prev-white.png" alt="이전">
            </button>
            <div class="pagination-number-box">
              <input type="number" v-model="currentPage" class="pagination__input">
              <mark class="pagination__total-number">/ 27</mark>
            </div>
            <button class="pagination-button pagination-button-next">
              <img src="@/assets/images/pagination-next-white.png" alt="다음">
            </button>
          </div>
        </div>
      </article>
    </div>
  </article>
</template>

<script>
import LineChart from '@/utils/LineChart'
export default {
  name: 'LinkedDetailInfoModal',
  components: {
    LineChart
  },
  data () {
    return {
      Mychart: null,
      DataObj: null,
      machinCocde: [],
      tar: {},
      minVal: undefined,
      maxVal: undefined,
      tlabels: [],
      ttime: [],
      tdata: [],
      lineChartData: {},
      isCritical: true,
      isWarning: true,
      isInfo: true,
      currentPage: 1,
      chartData: {},
      options: {
        maintainAspectRatio: false,
        responsive: true,
        legend: {
          display: false
        },
        scales: {
          xAxes: [{
            // stacked: false,
            type: 'time',
            time: {
              unit: 'second',
              displayFormats: {
                second: 'HH:mm:ss',
                minute: 'HH:mm:ss',
                hour: 'HH:mm:ss'
              },
              // min: minVal,
              min: this.minVal,
              max: this.maxVal
            },
            distribution: 'series',
            ticks: {
              fontColor: '#fff',
              fontSize: 10,
              autoSkip: true,
              maxRotation: 45,
              minRotation: 45
            },
            gridLines: {
              color: 'rgba(255,255,255,.2)',
              lineWidth: 1,
              zeroLineColor: '#fff'
            }
          }],
          yAxes: [{
            distribution: 'series',
            ticks: {
              stepSize: 5,
              fontColor: '#fff',
              fontSize: 14,
              fontFamily: "'NanumSquare', sans-serif, 'Malgun Gothic', '맑은 고딕'"
            },
            gridLines: {
              color: 'rgba(255,255,255,.2)',
              lineWidth: 1,
              zeroLineColor: '#fff'
            }
          }]
        }
      }
    }
  },
  props: {
    data: {
      type: Object
    }
  },
  methods: {
    parsing (response) {
      this.DataObj = response.data
      console.log('DataObj=', this.DataObj)
      // 변수 초기화

      // parsing JSON string
      var tarIdx = 0
      var StringParam = 'param' // 데이터 인자 param 키값
      var StringValue = 'value' // 데이터 인자 value 키값
      var StringCreated = 'created' // 데이터 인자 created 키값
      // 데이터가 없을 경우 => 빈그래프
      if (this.DataObj.length !== 0) {
        // 데이터 객체에 접근하는 키값 구하기
        const keyList = Object.keys(this.DataObj[0])
        const keyMark = [false, false, false]
        for (var key of keyList) {
          // param에 해당하는 키
          if (!keyMark[0] && key.toLocaleLowerCase().indexOf(StringParam) !== -1) { StringParam = key; keyMark[0] = true }
          // value에 해당하는 키
          if (!keyMark[1] && key.toLocaleLowerCase().indexOf(StringValue) !== -1) { StringValue = key; keyMark[1] = true }
          // created에 해당하는 키
          if (!keyMark[2] && key.toLocaleLowerCase().indexOf(StringCreated) !== -1) { StringCreated = key; keyMark[2] = true }
        }
        // 데이터타입이 인식될 수 없는 경우 => 빈그래프
        if (keyMark[0] && keyMark[1] && keyMark[2]) {
          // 해당 머신코드에 대한 데이터만 tar에 묶음
          for (let i = 0; i < this.DataObj.length; ++i) {
            if (this.machineCode === this.DataObj[i].machineCode) this.tar[tarIdx++] = this.DataObj[i]
          }
          // 데이터 객체에서 인자값들을 읽어오기
          for (let i = 0; i < tarIdx; ++i) {
            const idx = this.tlabels.indexOf(this.tar[i][StringParam])
            // console.log('ttime=', this.ttime)
            if (idx === -1) { // param 값이 이전에 없던 값일 경우
              this.tlabels.push(this.tar[i][StringParam])
              this.ttime.push([this.tar[i][StringCreated]])
              this.tdata.push([this.tar[i][StringValue]])
              console.log('tlabels=', this.tlabels, this.ttime, this.tdata)
            } else {
              this.ttime[idx].push(this.tar[i][StringCreated])
              this.tdata[idx].push(this.tar[i][StringValue])
            }
          // console.log('tdata=', this.tdata)
          }
        }
      }
    },
    getchartData () {
      // 'Blue', 'Purple', 'Red', 'Yellow', 'Green', 'Orange'
      var colorPal = ['rgb(54,162,235)', 'rgb(153,102,255)', 'rgb(255,99,132)', 'rgb(255,206,86)', 'rgb(75,192,192)', 'rgb(255,159,64)']
      this.lineChartData.labels = this.ttime[0]
      this.lineChartData.datasets = []
      for (let i = 0; i < this.tlabels.length; ++i) {
        this.lineChartData.datasets.push({})
        this.lineChartData.datasets[i].label = this.tlabels[i]
        this.lineChartData.datasets[i].data = []
        if (this.tdata[i] !== undefined) {
          for (let j = 0; j < this.tdata[i].length; ++j) {
            this.lineChartData.datasets[i].data.push({})
            this.lineChartData.datasets[i].data[j].t = this.ttime[i][j]
            this.lineChartData.datasets[i].data[j].y = this.tdata[i][j]
          }
        }
        this.lineChartData.datasets[i].fill = false
        this.lineChartData.datasets[i].backgroundColor = colorPal[i % 6]
        this.lineChartData.datasets[i].borderColor = colorPal[i % 6]
        this.lineChartData.datasets[i].pointBorderWidth = 1
        this.lineChartData.datasets[i].borderWidth = 3
        this.lineChartData.datasets[i].lineTension = 0.1
        this.lineChartData.datasets[i].SpanGaps = true
        this.chartData = this.lineChartData
        console.log('linechartData=', this.lineChartData.datasets)
      }
    },
    draw () {
      // 머신코드 읽어오기
      this.machineCode = 'he03'
      // var self = this
      // Axios로 서버에 request
      var axios = require('axios')
      axios({
        method: 'GET', // 통신 방식
        // 추후 수정 필요
        url: 'http://118.67.130.122:18001/machine/getdata/he03' // 통신할 페이지
      })
        .then(response => {
          // 파싱 모듈
          this.parsing(response)
          console.log('response=', response)
          // 차트데이터 모듈
          this.getchartData()
        })
        .catch(error => { console.error(error) })
    }
  },
  created () {
    this.draw()
  }
}
</script>

<style lang="scss">
@import "src/assets/style/components/modal";
@import "src/assets/style/components/list";
.linked-detail-info-modal {
  background-repeat: no-repeat;
  background-image: url('../assets/images/linked-facility-bg.png');
  background-position: 50% 50%;
  background-size: cover;
  .info-modal-content {
    background-color: transparent;
    padding: 1.66rem 1.66rem 5.54rem;
  }
  .info-modal-content {
    overflow-y: auto;
    height: 74vh;
    &-content {
      border-radius: 10px;
      box-shadow: 0px 4px 7px 0 rgba(72, 68, 66, 0.15);
      background: rgba(255, 255, 255, 0.3);
      overflow: hidden;
      border: 1px solid rgba(255,255,255,0.3);

      .info-modal__title {
        background-color: rgba(60, 180, 159, 0.3);
        color: $white;
        font-size: 1.16rem;
        padding: 1rem;
      }
      .chart__label {
        margin-left: 40px;
        &-box {
          font-size: 0.8rem;
          font-weight: 400;
          padding-left: 45px;
          position: relative;
          &:before {
            content: '';
            width: 40px;
            height: 19px;
            display: inline-block;
            position: absolute;
            border-radius: 4px;
            left: 0;
            top: 0;
          }
          &.humidty {
            margin-right: 20px;
            &:before {
              background: #32cdf4;
            }
          }
          &.count {
            &:before {
              background: #dcb0ff;
            }
          }
        }
      }
      .info-modal-info {
        background: none;

        &-chart {
          padding: 2rem 1rem 1rem;
          height: calc(100% - 4rem);
          box-sizing: border-box;
        }
        > div {
          position: relative;
          height: 100%;
        }
        &-part {
          display: flex;
          align-items: center;
          border-bottom: 1px solid rgba(208, 208, 208, 0.3);
          height: 3.33rem;
          &:last-of-type {
            border-bottom: 0;
          }
        }
        &__subject {
          color: #90e9ff;
          font-weight: 800;
          padding-left: 1.08rem;
          width: 177px;
          box-sizing: border-box;
        }
        &__content {
          color: #fff;
          font-weight: normal;
          font-size: 0.9rem;
        }
      }
    }
    &-top {
      display: flex;
    }
    &-info {
      width: 39.3%;
      margin-right: 2%;
      height: 580px;
    }
    &-graph {
      width: 59.7%;
      height: 580px;
    }
    &-table {
      margin-top: 1.375rem;
      &--data {
        .info-modal-table {
          thead {
            tr {
              border-bottom: 1px solid rgba(255,255,255,0.6);
            }
            th {
              color: #90e9ff;
            }
          }
          tbody {
            tr {
              border-bottom: 1px solid rgba(255,255,255,0.3);
            }
          }
        }
        .info-modal-table-pagination {
          color: #fff;
          .pagination__input {
            border: solid 1px #fff;
            color: #fff;
          }
        }
      }
      &--error {
        .info-modal__title {
          background: rgba(255, 42, 0, 0.3);
        }
        .info-modal-table {
          thead {
            tr {
              //border-bottom: 1px solid rgba(226,112,94,0.6);
            }
            th {
              //color: #e2705e;
            }
          }
          tbody {
            tr {
              //border-bottom: 1px solid rgba(226,112,94,0.3);
            }
          }
        }
        //.info-modal-table-pagination {
        //  color: #e2705e;
        //  .pagination__input {
        //    border: solid 1px #e2705e;
        //    color: #e2705e;
        //  }
        //}
      }
    }
    .info-modal-table {
      width: 100%;
      background: rgba(255,255,255,0.3);
      thead {
        tr {
          border-bottom: 1px solid rgba(255,255,255,0.6);
        }
        th {
          color: #90e9ff;
        }
      }
      tbody {
        tr {
          border-bottom: 1px solid rgba(255,255,255,0.3);
        }
      }
      tbody {
        tr:last-of-type {
          border-bottom: none;
        }
      }
      th {
        text-align: center;
        font-weight: 800;
        padding: 1.2rem 0 1rem 0;
      }
      td {
        color: #fff;
        text-align: center;
        padding: 1rem 0;
        font-size: 0.9rem;
      }
      &-pagination {
        background-color: rgba(218,218,218,.1);
        display: flex;
        justify-content: flex-end;
        align-items: center;
        height: 74px;
        padding: 0 1rem;
        box-sizing: border-box;
        color: #fff;
        .pagination {
          &__input {
            width: 89px;
            height: 40px;
            text-align: right;
            border-radius: 4px;
            background: none;
            font-size: 1rem;
            padding-right: 0.5rem;
            box-sizing: border-box;
            margin-right: 0.25rem;
            color: #fff;
            border: 1px solid #fff;
          }
          &-number-box {
            margin: 0 1rem;
          }
        }
      }
      &--data {

      }
    }
  }
}
</style>
