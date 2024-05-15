<template>
  <div class="Main">
        <h3>선택기술</h3>
        <button class="tech-button">Java</button>
        <button class="tech-button">Spring</button>
        <button class="tech-button">SQL</button>
        <h3>Inflearn</h3>
        <h3>Youtube</h3>
        <h3>K-MOOC</h3>
  </div>
</template>

<script>
export default {
  name: 'MainItem'
}
</script>

<style scoped>
 .tech-button {
    padding: 10px; /* 내부 여백 추가 */
    margin-left: 10px;
    border: none; /* 테두리 없음 */
    background-color: #b3a9ee; /* 배경색 설정 */
    color: rgb(0, 0, 0); /* 텍스트 색상 설정 */
    border-radius: 10px; /* 둥근 모서리를 가진 버튼으로 만듦 */
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
    width: 70px;
 }
 .tech-button:hover {
    background-color: #897bd8;
 }
 .Main {
    float: left;
    padding-left: 1%;
 }
</style>
