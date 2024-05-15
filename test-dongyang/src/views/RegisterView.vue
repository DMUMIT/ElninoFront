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
/* eslint-disable */
name: 'RegisterView',
    data() {
            return {
                email: '',
                password: '',
                confirm: ''
            }
    },
    methods: {
            submit(){

            }
    }
}
</script>