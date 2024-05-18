<template>
    <div class="login">
        <div class="login-box">
            <form @submit="submit">
                <img alt="logo" class="logo" src="../assets/elnino.png">
                <h2>Sign Up</h2>
                <div class="input-container">
                    <input type="email" id="email" name="email" required class="login-input" placeholder="Email">
                </div>
                <div class="input-container">
                    <p style="text-align:left; font-size:13px">Create Password</p>
                    <input type="password" id="password" name="password" required class="login-input" placeholder="Password">
                </div>
                <div class="input-container">
                    <p style="text-align:left; font-size:13px">Confirm Password</p>
                    <input type="password" id="confirm" name="confirm" required class="login-input" placeholder="Password">
                </div>
                <br>
                <button type="submit" class="signup-button">회원가입</button>
            </form>
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
        password: '',
        confirm: ''
      }
    }
  },
  methods: {
    submit () {
      console.log(this.formData)
      this.$router.push('/login')
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
</style>
