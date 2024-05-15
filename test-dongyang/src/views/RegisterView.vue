<template>
    <div class="login">
        <div class="login-box">
            <form @submit="submit">
                <img alt="logo" class="logo" src="../assets/elnino.png">
                <h2>Sign Up</h2>
                <div>
                    <label for="email">Email</label><br>
                    <input type="email" id="email" name="email" required>
                </div>
                <div>
                    <label for="password">Create Password</label><br>
                    <input type="password" id="password" name="password" required>
                </div>
                <div>
                    <label for="confirm-password">Confirm Password</label><br>
                    <input type="password" id="confirm" name="confirm" required>
                </div>
                <br>
                <button type="submit">회원가입</button>
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