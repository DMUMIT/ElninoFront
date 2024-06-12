<template>
  <div class="Main">
    <!-- 계정 당 DB에 저장된 설문조사 값에 따른 데이터 표시 -->
      <h3>선택기술</h3>
         <button v-for="tech in techList" :key="tech" class="tech-button">{{tech}}</button>
      <br>
      <h3 v-if="showYoutube">Youtube</h3>
        <div v-if="showYoutube" class="ItemList">
          <div class="content" v-for="(yt, index) in ytList" :key="index">
            <iframe :src="yt.url" width="300" height="190" class="player" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
            <p>{{ yt.title }}</p>
          </div>
        </div>
      <h3 v-if="showInflearn">Inflearn</h3> <!-- 테스트 단락 -->
         <div v-if="showInflearn" style="display: flex; overflow-x: auto;">
            <a v-for="(inf, index) in infList" :key="index" :href="inf"><img :alt="'image' + (index + 1)" :src="getImageSource(index)" style="margin-right: 10px;"></a>
         </div>
      <h3 v-if="showCodeit">코드잇</h3>
      <h3 v-if="showKmooc">K-MOOC</h3>
  </div>
</template>

<script>
export default {
  name: 'MainItem',
  data() {
    return {
      techList: ['Java', 'Spring', 'SQL', 'Nodejs'],
      cateList: ['youtube', 'inflearn'],
      infList: [
        'https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B8%B0%EB%B3%B8%ED%8E%B8',
        'https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-db-2',
        'https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-JPA-%ED%99%9C%EC%9A%A9-1'
      ],
      ytList: [
        { url: 'https://www.youtube.com/embed/jdTsJzXmgU0?si=fOC2f7_3qiSgFj24', title: '자바 수업을 리뉴얼 했습니다' },
        { url: 'https://www.youtube.com/embed/qR90tdW0Hbo?si=-pYicpLqVfnLPVuB', title: 'Java - 소개와 수업 소개' },
        { url: 'https://www.youtube.com/embed/kyFrm3zKryE?si=O0pX4HuFpd4EccBf', title: 'Java - 설치' },
        { url: 'https://www.youtube.com/embed/2HNmQaMQiw4?si=FSYTQ5MmY45ps182', title: 'Java - 설치와 실행2 : 리눅스에 Java ...' }
      ],
      ciList: [],
      kmList: []
    }
  },
  computed: {
    showYoutube() {
      return this.cateList.includes('youtube')
    },
    showInflearn() {
      return this.cateList.includes('inflearn')
    },
    showCodeit() {
      return this.cateList.includes('codeit')
    },
    showKmooc() {
      return this.cateList.includes('kmooc')
    }
  },
  methods: {
    getImageSource(index) {
      const images = [
        require('../assets/spring1.png'),
        require('../assets/spring2.png'),
        require('../assets/spring3.png')
      ];
      return images[index] || '';
    }
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
 .player {
    margin-right: 10px;
 }
 .ItemList {
    overflow-x: auto;
    white-space: nowrap;
    display: flex;
  }
 .content {
    text-align: left;
    font-size: 17px;
    font-weight: bold;
  }
</style>
