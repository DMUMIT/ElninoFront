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


<style>
    .logo {
        width: 230px;
        height: 60px;
        display: block;
    }
    .main-logo {
        width: 230px;
        height: 60px;
    }
    .login-box {
        width: 450px; /* 원하는 너비로 조정 */
        margin: auto; /* 가운데 정렬을 위해 */
        border: 1px solid #ebebeb; /* 선택적으로 박스에 테두리 추가 */
        border-radius: 50px;
        background-color: #ebebeb;
        padding: 50px; /* 내용과 테두리 사이의 간격 조정 */
    }
    .input-container {
        margin-bottom: 15px; /* input 요소와 다음 요소 사이의 간격 조정 */
    }

    .login-input {
        width: calc(100% - 22px); /* 100% 너비에서 padding 및 border 크기를 제외한 크기로 설정 */
        padding: 15px; /* 내부 여백 추가 */
        border: 1px solid #cccccc00; /* 테두리 설정 */
        border-radius: 5px; /* 둥근 모서리를 가진 input으로 만듦 */
        background-color: #e6e6e6;
    }
    .signup-button {
        width: 100%; /* 버튼을 100% 너비로 설정하여 부모 요소의 너비에 맞춤 */
        padding: 15px; /* 내부 여백 추가 */
        margin-top: 10px; /* 위쪽 여백 추가 */
        border: none; /* 테두리 없음 */
        background-color: #535353; /* 배경색 설정 */
        color: white; /* 텍스트 색상 설정 */
        border-radius: 5px; /* 둥근 모서리를 가진 버튼으로 만듦 */
        cursor: pointer; /* 마우스 커서를 포인터로 설정하여 클릭 가능한 상태 표시 */
    }
    .signup-button:hover {
        background-color: #2c2c2c; /* 호버 시 배경색 변경 */
    }
    .login-button {
        width: 100%; /* 버튼을 100% 너비로 설정하여 부모 요소의 너비에 맞춤 */
        padding: 15px; /* 내부 여백 추가 */
        margin-top: 10px; /* 위쪽 여백 추가 */
        border: none; /* 테두리 없음 */
        background-color: #67e2c3; /* 배경색 설정 */
        color: white; /* 텍스트 색상 설정 */
        border-radius: 5px; /* 둥근 모서리를 가진 버튼으로 만듦 */
        cursor: pointer; /* 마우스 커서를 포인터로 설정하여 클릭 가능한 상태 표시 */
    }
    .login-button:hover {
        background-color: #57bea5; /* 호버 시 배경색 변경 */
    }
</style>