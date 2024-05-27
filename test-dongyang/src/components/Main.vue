<template>
  <div class="Main">
      <h3>선택기술</h3>
         <button class="tech-button">Java</button>
         <button class="tech-button">Spring</button>
         <button class="tech-button">SQL</button>
      <br>
      <h3>Youtube</h3>
         <TestList/> <!-- 테스트 페이지 -->
      <hr>
      <h3>Inflearn</h3> <!-- 테스트 단락 -->
         <div style="display: flex; overflow-x: auto;">
            <a href="https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B8%B0%EB%B3%B8%ED%8E%B8"><img alt="test" style="margin-right: 10px;" src="../assets/spring1.png"></a>
            <a href="https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-db-2"><img alt="test" style="margin-right: 10px;" src="../assets/spring2.png"></a>
            <a href="https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-JPA-%ED%99%9C%EC%9A%A9-1"><img alt="test" style="margin-right: 10px;" src="../assets/spring3.png"></a>
            <a href="https://www.inflearn.com/course/sql-db-mysql-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B6%84%EC%84%9D"><img alt="test" style="margin-right: 10px;" src="../assets/sql.png"></a>
         </div>
      <!-- 이후 추가
         <h3>코드잇</h3>
         <h3>K-MOOC</h3>
      -->
  </div>
</template>

<script>
import TestList from '@/components/TestList.vue'

export default {
  name: 'MainItem',
  components: {
    TestList
  }
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
    font-weight: bold;
 }
 .tech-button:hover {
    background-color: #897bd8;
 }
 .Main {
    padding-left: 1%;
    text-align: left;
 }
</style>
