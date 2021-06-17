<template>
  <div>
    <DetailInfoModal />
    <DetailInfoModal :list-array="pageArray" :elist-array="epageArray" />
  </div>
</template>

<script>
import axios from 'axios'
import DetailInfoModal from './DetailInfoModal'
export default {
  name: 'DetailInfo-data',
  components: {
    DetailInfoModal
  },
  data () {
    return {
      pageArray: [],
      epageArray: []
    }
  },
  created () {
    axios.get('http://118.67.130.122:18001/machine/getdata/he06/num/').then(response => {
      console.log(response)
      this.pageArray = response.data.contacts
    }).catch(err => {
      console.log(err)
    })
    axios.get('http://118.67.130.122:18001/machine/geterr/he06/num/').then(response => {
      console.log(response)
      this.epageArray = response.data.contacts
    }).catch(err => {
      console.log(err)
    })
  }
}
</script>
