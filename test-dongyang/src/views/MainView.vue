<template>
  <div class="home">
    <img alt="logo" class="logo" src="../assets/elnino.png">
    <MainItem/>
    <MemoItem/>
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
  }
}
</script>
