<template>
    <div class="login">
        <div class="login-box">
            <form @submit.prevent="loginSubmit">
                <img alt="logo" class="logo" src="../assets/elnino.png">
                <h2>Welcome</h2>
                <div class="input-container">
                    <input type="email" id="email" name="email" class="login-input" placeholder="Email" v-model="formData.email">
                    <p v-if="validationErrors.email" style="color: red; font-size: 13px;">{{ validationErrors.email }}</p>
                </div>
                <div class="input-container">
                    <input type="password" id="password" name="password" class="login-input" placeholder="Password" v-model="formData.password">
                    <p v-if="validationErrors.password" style="color: red; font-size: 13px;">{{ validationErrors.password }}</p>
                </div>
                <p v-if="validationErrors.general" style="color: red; font-size: 13px;">{{ validationErrors.general }}</p>
                <button type="submit" class="login-button">로그인</button>
            </form>
            <hr>
            <button type="button" class="signup-button" onclick="location.href='/register'">회원가입</button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'RegisterView',
  data () {
    return {
      formData: {
        email: '',
        password: ''
      },
      validationErrors: {
        email: '',
        password: '',
        general: ''
      }
    }
  },
  methods: {
    validateForm () {
      this.validationErrors = {
        email: '',
        password: '',
        general: ''
      }
      if (!this.formData.email) {
        this.validationErrors.email = '이메일을 입력해주세요.'
      }
      if (!this.formData.password) {
        this.validationErrors.password = '비밀번호를 입력해주세요.'
      }
      return Object.values(this.validationErrors).every(error => !error)
    },
    loginSubmit () {
      if (this.validateForm()) {
        const validEmail = 'test@a.com'
        const validPassword = '1234'

        if (this.formData.email === validEmail && this.formData.password === validPassword) {
          // 데이터 넘기는 코드 추가
          const target = this.formData
          const jsonString = JSON.stringify(target)
          console.log(jsonString)
          this.$router.push('/select')
        } else {
          this.validationErrors.general = '로그인 정보가 맞지 않습니다. 다시 시도해주세요.'
        }
      }
    }
  }
}
</script>

<style>
    .logo {
        width: 230px;
        height: 60px;
        display: block;
    }
    .login {
        padding-top: 7%;
    }
    .login-box {
        width: 450px;
        margin: auto;
        border: 1px solid #ebebeb;
        border-radius: 50px;
        background-color: #ebebeb;
        padding: 50px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    .input-container {
        margin-bottom: 15px;
    }
    .login-input {
        width: calc(100% - 22px);
        padding: 15px;
        border: 1px solid #cccccc00;
        border-radius: 5px;
        background-color: #e6e6e6;
    }
    .signup-button {
        width: 100%;
        padding: 15px;
        margin-top: 10px;
        border: none;
        background-color: #535353;
        color: white;
        border-radius: 5px;
        cursor: pointer;
    }
    .signup-button:hover {
        background-color: #2c2c2c;
    }
    .login-button {
        width: 100%;
        padding: 15px;
        margin-top: 10px;
        border: none;
        background-color: #67e2c3;
        color: white;
        border-radius: 5px;
        cursor: pointer;
    }
    .login-button:hover {
        background-color: #57bea5;
    }
</style>
