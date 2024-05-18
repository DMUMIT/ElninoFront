<template>
  <div class="manual">
    <h1>Welcome to Elnino</h1>
    <h4>위 사이트는 컴퓨터공학부용 사이트입니다.</h4>
    사용을 원하시면 아래와 같이 설문에 참여하신 후 이용 가능합니다.<br>
    <h4>1. 회원가입 후 로그인을 해주세요.</h4><br>
    <img alt="m0" class="man-img" src="../assets/manual0.jpg"><br>
    <h4>2. 로그인 후 이동되는 설문조사 페이지에서 본인의 선택을 해주세요.</h4><br>
    선택사항은 본인의 학년, 카테고리, 선호 기술 입니다. 선호 기술에 따라 상위에 노출될 결과들이 달라집니다.<br>
    <img alt="m1" class="man-img" src="../assets/manual1.jpg"><br>
    <img alt="m2" class="man-img" src="../assets/manual2.jpg"><br>
    <img alt="m3" class="man-img" src="../assets/manual3.jpg"><br>
    <button type="button" onclick="location.href='/login'">시작</button>
  </div>
</template>

<script>
export default {
  name: 'AboutView'
}
</script>
