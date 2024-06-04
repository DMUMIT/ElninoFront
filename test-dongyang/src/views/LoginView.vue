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
      <button type="submit" class="signup-button" onclick="location.href='/register'">회원가입</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      formData: {
        email: '',
        password: ''
      },
      validationErrors: {}
    }
  },
  methods: {
    async login() {
      this.validationErrors = this.validateForm()
      if (Object.keys(this.validationErrors).length === 0) {
        try {
          const response = await axios.post('http://localhost:8080/users/login', {
            email: this.formData.email,
            password: this.formData.password
          })
          console.log(response.data)
          if (response.data === 'Login successful') {
            this.$router.push('/select')
          } else {
            this.validationErrors.general = 'Invalid email or password'
          }
        } catch (error) {
          console.error('Error logging in user:', error)
          this.validationErrors.general = 'Server error'
        }
      }
    },
    validateForm() {
      const errors = {}
      if (!this.formData.email) {
        errors.email = '이메일을 입력해주세요'
      }
      if (!this.formData.password) {
        errors.password = '비밀번호를 입력해주세요'
      }
      return errors
    }
  }
}
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
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 1rem;
}

.login-button {
  width: 100%;
  padding: 0.75rem;
  background-color: #007bff;
  border: none;
  border-radius: 5px;
  color: white;
  font-size: 1rem;
  cursor: pointer;
}

.signup-button {
        width: 100%;
        padding: 15px;
        margin-top: 10px;
        border: none;
        background-color: #007bff;
        color: white;
        border-radius: 5px;
        cursor: pointer;
    }

.login-button:hover {
  background-color: #0056b3;
}
.signup-button:hover {
  background-color: #0056b3;
}
</style>
