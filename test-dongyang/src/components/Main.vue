<template>
  <div class="Main">
    <li>
      <ul>
        <h3>선택기술</h3>
        <button>test1</button>
        <button>test1</button>
        <button>test1</button>
      </ul>
      <ul>
        <h3>Inflearn</h3>
      </ul>
      <ul>
        <h3>Youtube</h3>
      </ul>
      <ul>
        <h3>K-MOOC</h3>
      </ul>
    </li>
  </div>
</template>

<script>
export default {
  name: 'MainItem'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
