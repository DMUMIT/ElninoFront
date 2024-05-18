<template>
    <div class="login">
        <div class="login-box">
            <form @submit.prevent="loginSubmit">
                <img alt="logo" class="logo" src="../assets/elnino.png">
                <h2>Welcome</h2>
                <div class="input-container">
                    <input type="email" id="email" name="email" required class="login-input" placeholder="Email" v-model="formData.email">
                </div>
                <div class="input-container">
                    <input type="password" id="password" name="password" required class="login-input" placeholder="Password" v-model="formData.password">
                </div>
                <br>
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
      }
    }
  },
  methods: {
    loginSubmit () {
      console.log(this.formData)
      this.$router.push('/select')
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
