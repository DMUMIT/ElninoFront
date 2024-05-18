<template>
  <div class="manual">
    <img alt="logo" class="main-logo" src="../assets/elnino.png">
    <h1>Welcome to Elnino</h1>
    <h4>위 사이트는 컴퓨터공학부용 사이트입니다.</h4>
    <p>사용을 원하시면 아래와 같이 설문에 참여하신 후 이용 가능합니다.</p>
    <h4>1. 회원가입 후 로그인을 해주세요.</h4>
    <img alt="m0" class="man-img" src="../assets/manual0.jpg">
    <h4>2. 로그인 후 이동되는 설문조사 페이지에서 본인의 선택을 해주세요.</h4>
    <p>선택사항은 본인의 학년, 카테고리, 선호 기술 입니다. 선호 기술에 따라 상위에 노출될 결과들이 달라집니다.</p>
    <img alt="m1" class="man-img" src="../assets/manual1.jpg"><br>
    <img alt="m2" class="man-img" src="../assets/manual2.jpg"><br>
    <img alt="m3" class="man-img" src="../assets/manual3.jpg"><br>
    <p style="font-weight: bold; font-size: 18px;">설문조사를 전부 작성하시게 된다면, Elnino와의 여정을 시작하실수 있게 됩니다.</p>
    <button type="button" class="next-button" onclick="location.href='/login'">시작하기</button>
  </div>
</template>

<script>
export default {
  name: 'AboutView'
}
</script>

<style>
  .manual {
    padding-bottom: 60px;
  }
  .main-logo {
    padding-top: 10px;
    width: 230px;
    height: 60px;
  }
  .next-button {
    width: 50%;
    padding: 15px;
    margin-top: 10px;
    border: none;
    background-color: #67e2c3;
    color: white;
    border-radius: 5px;
    cursor: pointer;

    position: fixed;
    bottom: 1%;
    left: 25%;
  }
  .next-button:hover {
    background-color: #57bea5;
  }
  .man-img {
    width: 600px;
    margin: auto;
    border: 1px solid #ebebeb;
    border-radius: 20px;
    background-color: #ebebeb;
    padding: 1px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
</style>
