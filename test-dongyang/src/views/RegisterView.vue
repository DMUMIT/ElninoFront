<template>
  <div class="login">
    <div class="login-box">
      <form @submit.prevent="accountSubmit">
        <img alt="logo" class="logo" src="../assets/elnino.png">
        <h2>Sign Up</h2>
        <div class="input-container">
          <input type="email" id="email" name="email" class="login-input" placeholder="Email" v-model="formData.email" />
          <p v-if="validationErrors.email" style="color: red; font-size: 13px;">{{ validationErrors.email }}</p>
        </div>
        <div class="input-container">
          <p style="text-align:left; font-size:13px">Username</p>
          <input type="text" id="username" name="username" class="login-input" placeholder="Username" v-model="formData.username" />
          <p v-if="validationErrors.username" style="color: red; font-size: 13px;">{{ validationErrors.username }}</p>
        </div>
        <div class="input-container">
          <p style="text-align:left; font-size:13px">Create Password</p>
          <input type="password" id="password" name="password" class="login-input" placeholder="Password" v-model="formData.password" />
          <p v-if="validationErrors.password" style="color: red; font-size: 13px;">{{ validationErrors.password }}</p>
        </div>
        <div class="input-container">
          <p style="text-align:left; font-size:13px">Confirm Password</p>
          <input type="password" id="confirm" name="confirm" class="login-input" placeholder="Password" v-model="formData.confirm" />
          <p v-if="validationErrors.confirm" style="color: red; font-size: 13px;">{{ validationErrors.confirm }}</p>
        </div>
        <button type="submit" class="signup-button">회원가입</button>
        <hr>
        <button type="submit" class="login-button" onclick="location.href='/login'">로그인</button>
      </form>
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
        username: '',
        password: '',
        confirm: ''
      },
      validationErrors: {}
    }
  },
  methods: {
    async accountSubmit() {
      this.validationErrors = this.validateForm()
      if (Object.keys(this.validationErrors).length === 0) {
        try {
          const response = await axios.post('http://localhost:8080/users/register', {
            email: this.formData.email,
            username: this.formData.username,
            password: this.formData.password
          })
          console.log(response.data)
          this.$router.push('/login') // 회원가입 성공 시 로그인 페이지로 이동
        } catch (error) {
          console.error('Error registering user:', error)
        }
      }
    },
    validateForm() {
      const errors = {}
      if (!this.formData.email) {
        errors.email = 'Email is required'
      }
      if (!this.formData.username) {
        errors.username = 'Username is required'
      }
      if (!this.formData.password) {
        errors.password = 'Password is required'
      }
      if (this.formData.password !== this.formData.confirm) {
        errors.confirm = 'Passwords do not match'
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
