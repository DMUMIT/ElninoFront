<template>
  <div class="main">
    <img alt="logo" class="main-logo" src="../assets/elnino.png">
    <div class="main-body">
      <div class="main-1">
        <MainItem/>
      </div>
      <div class="main-2">
        <p style="font-weight: bold; font-size: 25px;">{{ currentDateTime }}</p>
        <MemoItem/>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import MainItem from '@/components/Main.vue'
import MemoItem from '@/components/Memo.vue'

export default {
  name: 'HomeView',
  components: {
    MainItem,
    MemoItem
  },
  data () {
    return {
      currentDateTime: ''
    }
  },
  mounted () {
    this.updateDateTime() // 페이지 로드시 날짜 및 시간 업데이트
    setInterval(this.updateDateTime, 1000) // 1초마다 날짜 및 시간 업데이트
  },
  methods: {
    updateDateTime () {
      const now = new Date()
      const year = now.getFullYear()
      const month = String(now.getMonth() + 1).padStart(2, '0')
      const day = String(now.getDate()).padStart(2, '0')
      const hours = String(now.getHours()).padStart(2, '0')
      const minutes = String(now.getMinutes()).padStart(2, '0')
      const seconds = String(now.getSeconds()).padStart(2, '0')
      this.currentDateTime = `${year}.${month}.${day} ${hours}:${minutes}:${seconds}`
    }
  }
}
</script>

<style>
  .main-logo {
        width: 230px;
        height: 60px;
  }
  .main-body {
    display: flex;
  }
  .main-1 {
    width: 70%;
  }
  .main-2 {
    padding-top: 250px;
    background-color: white;
    width: 30%;
  }
</style>
