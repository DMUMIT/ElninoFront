<template>
  <div class="login">
    <div class="login-box">
      <form @submit.prevent="login">
        <img alt="logo" class="logo" src="../assets/elnino.png">
        <h2>Login</h2>
        <div class="input-container">
          <input type="email" id="email" name="email" class="login-input" placeholder="Email" v-model="formData.email" />
          <p v-if="validationErrors.email" style="color: red; font-size: 13px;">{{ validationErrors.email }}</p>
        </div>
        <div class="input-container">
          <input type="password" id="password" name="password" class="login-input" placeholder="Password" v-model="formData.password" />
          <p v-if="validationErrors.password" style="color: red; font-size: 13px;">{{ validationErrors.password }}</p>
        </div>
        <button type="submit" class="login-button">로그인</button>
      </form>
      <br>
      <button type="submit" class="signup-button" @click="goToRegister">회원가입</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      formData: {
        email: '',
        password: ''
      },
      validationErrors: {}
    };
  },
  methods: {
    goToRegister() {
      this.$router.push('/register');
    },
    async login() {
      this.validationErrors = {}; // Reset validation errors
      if (!this.formData.email) {
        this.validationErrors.email = 'Email is required';
      }
      if (!this.formData.password) {
        this.validationErrors.password = 'Password is required';
      }
      if (Object.keys(this.validationErrors).length > 0) {
        return;
      }

      try {
        const response = await axios.post('http://localhost:8080/users/login', {
          email: this.formData.email,
          password: this.formData.password
        }, { withCredentials: true });

        console.log('Server response:', response.data);

        if (response.data.success) {
          const surveyResponse = await axios.get('http://localhost:8080/survey/checkSurvey', {
            params: { email: this.formData.email }
          });
          const userSurvey = surveyResponse.data.exists;

          if (userSurvey) {
            console.log('Survey already exists, redirecting to main page');
            this.$router.push('/main');
          } else {
            console.log('No survey found, redirecting to survey page');
            this.$router.push({ path: '/select', query: { email: this.formData.email } });
          }
        } else {
          console.log('Login failed:', response.data.message);
          alert(response.data.message);
        }
      } catch (error) {
        console.error('Error logging in:', error);
        alert('An error occurred during login');
      }
    }
  }
};
</script>

<style scoped>
/* 추가적인 스타일을 여기에 추가하세요 */
.login {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.login-box {
  background-color: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 400px;
  max-width: 100%;
}

.logo {
  display: block;
  margin: 0 auto 1rem;
  width: 150px;
}

h2 {
  text-align: center;
  margin-bottom: 1rem;
}

.input-container {
  margin-bottom: 1rem;
}

.login-input {
  width: 95%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 1rem;
}

.signup-button {
  width: 100%;
  padding: 0.75rem;
  background-color: #979a9c;
  border: none;
  border-radius: 5px;
  color: white;
  font-size: 1rem;
  cursor: pointer;
}

.signup-button:hover {
  background-color: #616161;
}

.login-button {
  width: 100%;
  padding: 0.75rem;
  background-color: #8ee6b5;
  border: none;
  border-radius: 5px;
  color: white;
  font-size: 1rem;
  cursor: pointer;
}

.login-button:hover {
  background-color: #609c7b;
    }
</style>
