/* eslint-disable */
<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
    <div class="select">
        <nav class="navbar navbar-light" style="background-color: rgb(162, 162, 255); height: 50px;">
            <span style="color: white;">Elnino</span>
        </nav>
        <br>
        <form class="submit-form" @submit.prevent="selectSubmit">
            <br>
            <div v-if="step === 1">
                <h5><span style="color: red;">몇 학년</span>인가요?</h5>
                <br>
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
                <p v-if="validationErrors.message" style="color: red; font-size: 13px;">{{ validationErrors.message }}</p>
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
                    <br>
                    <div v-for="tech in technologies[formData.category]" :key="tech" class="form-check">
                        <input class="form-check-input" type="checkbox" :id="tech" :value="tech" v-model="formData.technologies">
                        <label class="form-check-label" :for="tech">
                            {{ tech }}
                        </label>
                    </div>
                </div>
                <p v-if="validationErrors.message" style="color: red; font-size: 13px;">{{ validationErrors.message }}</p>
            </div>
            <div v-if="step === 3">
                <h5>어떤 <span style="color: red;">사이트</span>를 자주 사용하시나요? (중복선택 가능)</h5>
                <br>
                <div v-for="site in favoriteSite" :key="site" class="form-check">
                    <input class="form-check-input" type="checkbox" :id="site" :value="site" v-model="formData.favoriteSite">
                    <label class="form-check-label" :for="site">
                        {{ site }}
                    </label>
                </div>
                <p v-if="validationErrors.message" style="color: red; font-size: 13px;">{{ validationErrors.message }}</p>
            </div>
            <div v-if="step === 4">
                <h5>설문조사가 완료되었습니다, 감사합니다.</h5>
            </div>
            <div class="mt-3">
                <button type="button" class="select-button-left" @click="prevStep" v-if="step > 0">이전 페이지</button>
                <button type="button" class="select-button-right" @click="nextStep" v-if="step < 4">다음 페이지</button>
                <button type="submit" class="select-button-right" v-if="step === 4">시작하기</button>
            </div>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'SelectView',
  data() {
    return {
      step: 1,
      formData: {
        email: '',
        grade: '',
        category: '',
        technologies: [],
        favoriteSite: []
      },
      validationErrors: {
        message: ''
      },
      technologies: {
        백엔드: ['Java', 'Spring', 'Node.js', 'Django', 'Docker'],
        프론트엔드: ['html/css', 'vue.js', 'react', 'figma'],
        데이터베이스: ['MySQL(MariaDB)', 'Oracle', 'MongoDB', 'PostgreSQL', 'AWS'],
        풀스택: ['Java', 'Spring', 'Node.js', 'Django', 'Docker', 'html/css', 'vue.js', 'react', 'figma']
      },
      favoriteSite: ['Youtube', 'Inflearn', '코드잇', 'K-MOOC']
    };
  },
  created() {
    this.formData.email = this.$route.query.email;
    if (!this.formData.email) {
      alert('Email is required for the survey.');
      this.$router.push('/login');
    }
    this.checkExistingSurvey();
  },
  methods: {
    validateForm() {
      this.validationErrors = {
        message: ''
      };
      if (this.step === 1 && !this.formData.grade) {
        this.validationErrors.message = '학년을 선택해주세요.';
        return false;
      }
      if (this.step === 2 && (!this.formData.category || this.formData.technologies.length === 0)) {
        this.validationErrors.message = '카테고리와 선호 기술을 선택해주세요.';
        return false;
      }
      if (this.step === 3 && this.formData.favoriteSite.length === 0) {
        this.validationErrors.message = '선호 사이트를 선택해주세요.';
        return false;
      }
      return true;
    },
    nextStep() {
      if (this.validateForm()) {
        if (this.step < 4) {
          this.step++;
        }
      }
    },
    prevStep() {
      if (this.step > 1) {
        this.step--;
      }
    },
    async selectSubmit() {
      try {
        const response = await axios.post('http://localhost:8080/survey/submit', this.formData);
        console.log(response.data);
        if (response.data.redirectTo) {
          this.$router.push(response.data.redirectTo);
        } else {
          alert('Survey submitted successfully!');
          this.$router.push('/main');
        }
      } catch (error) {
        console.error('Error submitting survey:', error);
        alert('Error submitting survey');
      }
    },
    updateTechnologies() {
      this.formData.technologies = []; // 카테고리가 변경될 때 선택된 기술 초기화
    },
    async checkExistingSurvey() {
      try {
        const response = await axios.get('http://localhost:8080/survey/data');
        const surveys = response.data;
        const userSurvey = surveys.find(survey => survey.email === this.formData.email);

        if (userSurvey) {
          console.log('Survey already exists, redirecting to main page');
          this.$router.push('/main');
        }
      } catch (error) {
        console.error('Error checking existing survey:', error);
      }
    }
  }
};
</script>

<style scoped>
.submit-form {
    max-width: 500px;
    height: 520px;
    margin: auto;
    padding-top: 1%;
    padding-left: 1%;
    padding-right: 1%;
    background-color: white;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
.form-check {
    padding-left: 40%;
    display: flex;
}
.form-check-label {
    padding-left: 5%;
}
.select-button-left {
        width: 30%;
        padding: 3px;
        margin-top: 10px;
        margin-right: 50px;
        border: none;
        background-color: rgb(162, 162, 255);;
        color: white;
        border-radius: 5px;
        cursor: pointer;
}
.select-button-right {
        width: 30%;
        padding: 3px;
        margin-top: 10px;
        margin-left: 100px;
        border: none;
        background-color: rgb(162, 162, 255);;
        color: white;
        border-radius: 5px;
        cursor: pointer;
}
.select-button-left:hover, .select-button-right:hover {
    background-color: rgb(137, 137, 218);
}
</style>
