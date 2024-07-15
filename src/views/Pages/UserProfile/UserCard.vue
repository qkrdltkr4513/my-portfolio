<template>
  <b-card no-body class="card-profile" alt="Image placeholder" img-top>
    <b-row class="justify-content-center">
      <b-col lg="3" class="order-lg-2">
        <div class="card-profile-image">
          <a href="#/profile">
            <b-img
              src="img/portfolio/my-profile.png"
              style="max-width: 140px"
              rounded="circle"
            />
          </a>
        </div>
      </b-col>
    </b-row>

    <b-card-header
      class="text-center border-0 pt-8 pt-md-4 pb-0 pb-md-4"
    ></b-card-header>

    <b-card-body class="pt-0 profile-card-body">
      <b-row>
        <b-col>
          <div
            class="card-profile-stats d-flex justify-content-center ml-4 mt-md-6"
          >
            <div>
              <span class="heading">성별</span>
              <span class="description">남</span>
            </div>
            <div>
              <span class="heading">나이</span>
              <span class="description">33</span>
            </div>
            <div>
              <span class="heading">경력</span>
              <span class="description">7년 2개월</span>
            </div>
          </div>
        </b-col>
      </b-row>
      <div class="text-center">
        <h5 class="h3">박이삭</h5>
        <div class="h5 font-weight-300">
          경기도 수원시 광교중앙로 145 광교 엘포트아이파크 B동 421호
        </div>
        <div class="h5 mt-4">상명대학교</div>
        <div>컴퓨터소프트웨어공학과</div>
        <hr class="my-4" />
        <p>관심분야: Front-End</p>
        <p>휴대전화: 010-5629-0727</p>
        <p>E-Mail: qkrdltkr4513@gmail.com</p>
      </div>
    </b-card-body>
  </b-card>
</template>
<script>
export default {};
</script>
<style>
/* .profile-card-body */
</style>
