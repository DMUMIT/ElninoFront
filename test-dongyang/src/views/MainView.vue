<template>
  <div class="main">
    <img alt="logo" class="main-logo" src="../assets/elnino.png">
    <div class="account">
          {{username}} 님 환영합니다
          <button @click="logout">로그아웃</button>
    </div>
    <div class="main-body">
      <div class="main-1">
        <MainItem/>
      </div>
      <div class="main-2">
        <p style="font-weight: bold; font-size: 25px;">{{ currentDateTime }}</p>
        <p> {{username}} </p>
        <MemoItem/>
      </div>
    </div>
  </div>
</template>

<script>
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
    },
    logout() {
      // 로그아웃 동작 처리
      this.$store.dispatch('logout');
      this.$router.push('/login');
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
