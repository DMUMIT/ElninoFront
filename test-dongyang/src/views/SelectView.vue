<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <div class="select">
        <nav class="navbar navbar-light" style="background-color: rgb(162, 162, 255);">
            Elnino
        </nav>
        <br>
        <form class="submit-form" @submit.prevent="submit">
            <div v-if="step === 1">
                <h5><span style="color: red;">몇 학년</span>인가요?</h5>
                <div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="grade" id="grade1" value="1학년" v-model="formData.grade">
                        <label class="form-check-label" for="grade1">
                            1학년
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="grade" id="grade2" value="2학년" v-model="formData.grade">
                        <label class="form-check-label" for="grade2">
                            2학년
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="grade" id="grade3" value="3학년" v-model="formData.grade">
                        <label class="form-check-label" for="grade3">
                            3학년
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="grade" id="grade4" value="4학년" v-model="formData.grade">
                        <label class="form-check-label" for="grade4">
                            4학년
                        </label>
                    </div>
                </div>
            </div>
            <div v-if="step === 2">
                <h5>원하시는 <span style="color: red;">카테고리</span>를 선택해주세요</h5>
                <div>
                    <select v-model="formData.category" class="form-select" @change="updateTechnologies">
                        <option value="백엔드">백엔드</option>
                        <option value="프론트엔드">프론트엔드</option>
                        <option value="데이터베이스">데이터베이스</option>
                        <option value="풀스택">풀스택</option>
                    </select>
                </div>
                <br>
                <div v-if="formData.category">
                    <h5>선호 <span style="color: red;">{{ formData.category }} 기술</span>을 선택해주세요 (중복선택 가능)</h5>
                    <div v-for="tech in technologies[formData.category]" :key="tech" class="form-check">
                        <input class="form-check-input" type="checkbox" :id="tech" :value="tech" v-model="formData.technologies">
                        <label class="form-check-label" :for="tech">
                            {{ tech }}
                        </label>
                    </div>
                </div>
            </div>
            <div v-if="step === 3">
                <h5>어떤 <span style="color: red;">사이트</span>를 자주 사용하시나요? (중복선택 가능)</h5>
                <div>
                    <div class="form-check">
                        <input class="form-check-input" type="checkbox" name="favoriteSite" id="youtube" value="유튜브" v-model="formData.favoriteSites">
                        <label class="form-check-label" for="youtube">
                            유튜브
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="checkbox" name="favoriteSite" id="inflearn" value="인프런" v-model="formData.favoriteSites">
                        <label class="form-check-label" for="inflearn">
                            인프런
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="checkbox" name="favoriteSite" id="codeit" value="코드잇" v-model="formData.favoriteSites">
                        <label class="form-check-label" for="codeit">
                            코드잇
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="checkbox" name="favoriteSite" id="kmooc" value="K-MOOC" v-model="formData.favoriteSites">
                        <label class="form-check-label" for="kmooc">
                            K-MOOC
                        </label>
                    </div>
                </div>
            </div>
            <div class="mt-3">
                <button type="button" class="btn btn-secondary" @click="prevStep" v-if="step > 1" style="background-color: rgb(162, 162, 255);">이전 페이지</button>
                <button type="button" class="btn btn-primary" @click="nextStep" v-if="step < 3" style="background-color: rgb(162, 162, 255);">다음 페이지</button>
                <button type="submit" class="btn btn-success" v-if="step === 3" style="background-color: rgb(162, 162, 255);">홈으로</button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
  name: 'SelectView',
  data () {
    return {
      step: 1,
      formData: {
        grade: '',
        category: '',
        technologies: [],
        favoriteSite: []
      },
      technologies: {
        백엔드: ['Java', 'Spring', 'Node.js', 'Django', 'Docker'],
        프론트엔드: ['html/css', 'vue.js', 'react', 'figma'],
        데이터베이스: ['MySQL(MariaDB)', 'Oracle', 'MongoDB', 'PostgreSQL', 'AWS'],
        풀스택: ['Java', 'Spring', 'Node.js', 'Django', 'Docker', 'html/css', 'vue.js', 'react', 'figma']
      }
    }
  },
  methods: {
    nextStep () {
      if (this.step < 3) {
        this.step++
      }
    },
    prevStep () {
      if (this.step > 1) {
        this.step--
      }
    },
    submit () {
      // 여기에 제출 로직을 추가하세요.
      console.log(this.formData)
    },
    updateTechnologies () {
      this.formData.technologies = [] // 카테고리가 변경될 때 선택된 기술 초기화
    }
  }
}
</script>

<style scoped>
.submit-form {
    max-width: 500px;
    margin: auto;
    padding: 1em;
    background-color: white;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
</style>
