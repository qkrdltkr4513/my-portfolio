<template>
  <div class="portfolio-wrapper">
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 portfolio-background">
      <!-- Card stats -->
      <b-row>
        <b-col xl="3" md="6">
          <stats-card title="개인정보"
                      type="gradient-red"
                      sub-title="박이삭"
                      icon="ni ni-circle-08"
                      class="mb-4">

            <template slot="footer">
              <div class="first-line">
                <span class="text-success mr-2">나이:</span>
                <span class="text-nowrap mr-4">29세</span>
                <span class="text-success mr-2">성별:</span>
                <span class="text-nowrap">남자</span>
              </div>
              <div class="second-line">
                <span class="text-success mr-2">생년월일:</span>
                <span class="text-nowrap mr-4">1992.07.27</span>
              </div>
            </template>
          </stats-card>
        </b-col>
        <b-col xl="3" md="6">
          <stats-card title="병역사항"
                      type="gradient-orange"
                      sub-title="2012.01 ~ 2013.10"
                      icon="ni ni-user-run"
                      class="mb-4 military-period">

            <template slot="footer">
              <div class="first-line">
                <span class="text-success mr-2">군별:</span>
                <span class="text-nowrap mr-4">육군</span>
                <span class="text-success mr-2">계급:</span>
                <span class="text-nowrap">병장</span>
              </div>
              <div class="second-line">
                <span class="text-success mr-2">전역사유 :</span>
                <span class="text-nowrap mr-4">만기제대</span>
              </div>
            </template>
          </stats-card>
        </b-col>
        <b-col xl="3" md="6">
          <stats-card title="경력"
                      type="gradient-green"
                      sub-title="3년 7개월"
                      icon="ni ni-laptop"
                      class="mb-4">

            <template slot="footer">
              <span class="text-success block mr-2">재직 여부</span>
              <span class="text-nowrap block">현재 재직중</span>
            </template>
          </stats-card>

        </b-col>
        <b-col xl="3" md="6">
          <stats-card title="연락처"
                      type="gradient-info"
                      sub-title="010-5629-0727"
                      icon="ni ni-mobile-button"
                      class="mb-4 phone-number">

            <template slot="footer">
              <span class="text-success block mr-2">E-mail</span>
              <span class="text-nowrap block">qkrdltkr4513@gmail.com</span>
            </template>
          </stats-card>
        </b-col>
      </b-row>
    </base-header>
    <b-container fluid class="mt--7">
      <b-row>
        <b-col>
          <!-- <light-table/> -->
        </b-col>
      </b-row>
      <!-- <div class="mt-5"></div> -->
      <light-table></light-table>
    </b-container>
    <div class="container-fluid detail-card-block">
      <b-card v-for="(item, index) in projectList"
        :title="item.name"
        :img-src="item.img"
        img-alt="Image"
        img-top
        tag="article"
        style="margin: 0 auto; max-width: 60rem;"
        class="mb-6">
        <!-- <p class="title">사용기술</p> -->
        <span class="content-title">사용 기술</span>
        <b-card-text class="used-skill">{{item.skill}}</b-card-text>

        <span class="content-title">프로젝트 목적</span>
        <b-card-text class="intro">{{item.intro}}</b-card-text>

        <span class="content-title">담당 업무</span>
        <b-card-text>
          <p class="my-work" v-for="(work, workIndex) in item.workList">{{work}}</p>
        </b-card-text>

        <span class="content-title">형상 관리</span>
        <b-card-text class="manage-source">{{item.manageSource}}</b-card-text>

        <span class="content-title">프로젝트 기간</span>
        <b-card-text class="period">{{item.period}}</b-card-text>
        <!-- <b-card-body>
          This is some text within a card body.
        </b-card-body> -->

        <!-- <b-button href="javascript:;" variant="primary">Go somewhere</b-button> -->
      </b-card>
      <!-- <b-card
        title="Card Title"
        img-src="https://demos.creative-tim.com/argon-dashboard-pro/assets/img/theme/img-1-1000x600.jpg"
        img-alt="Image"
        img-top
        tag="article"
        style="margin: 0 auto 30px auto; max-width: 60rem;"
        class="mb-6">
        <b-card-text>
          Some quick example text to build on the card title and make up the bulk of the card's content.
        </b-card-text>

        <b-button href="javascript:;" variant="primary">Go somewhere</b-button>
      </b-card> -->
    </div>
  </div>
</template>
<script>
  import { Dropdown, DropdownItem, DropdownMenu, Table, TableColumn } from 'element-ui';
  import projects from './Tables/projects'
  import users from './Tables/users'
  import LightTable from "./Tables/RegularTables/LightTable";
  import DarkTable from "./Tables/RegularTables/DarkTable";

  export default {
    components: {
      LightTable,
      DarkTable,
      [Dropdown.name]: Dropdown,
      [DropdownItem.name]: DropdownItem,
      [DropdownMenu.name]: DropdownMenu,
      [Table.name]: Table,
      [TableColumn.name]: TableColumn
    },
    data() {
      return {
        projects,
        users,
        projectList: [
          {
            img: 'img/portfolio/img-iaq-cloud-dashboard.PNG',
            name: 'BuildThing IAQ Cloud (자사 서비스)',
            skill: 'Quasar Framework, Vue.js, jQuery, JavaScript, Stylus, Flask babel, GridStack.js, Open Api, Kendo UI',
            intro: '신규 개발 제품 IAQ (실내 공기질 측정), Gateway를 통해 공간 및 기기 관리를 통해 IAQ, Gateway 등록 관리 및 실내 공기질 수치 정보 제공',
            workList: [
              '· 프론트엔드 개발',
              '· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발',
              '· Gridstack.js를 사용하여 대시보드 카드 생성, 편집(위치 이동), 삭제 기능 구현',
              '· 자사에서 개발한 SDK와 각 종 UI 컴포넌트를 통해 담당 페이지 기능 구현 및 시각화',
              '· PG사 연동을 통한 결제 기능 구현 및 그룹 관리 기능 구현',
              '· Flask babel을 이용하여 SSR 렌더링을 통한 이용 약관에 관련된 페이지의 다국어 message.pot로 적용',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2020.08 ~ 2020.09'
          },
          {
            img: 'img/portfolio/img-cloud-beacon.PNG',
            name: 'BuildThing Cloud (자사 서비스)',
            skill: 'Quasar Framework, Vue.js, JavaScript, Flask Babel, Stylus, Kendo UI',
            intro: '자사 개발 제품 BuildThing Beacon(실내 공기질 측정)과 BuildThing Gateway를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 영역 마다 설치되어있는 비콘과 게이트웨이로부터 받아온 데이터를 기반으로 실시간 모니터링 및 웹 소켓을 통한 푸시 알람으로 영역을 관리하며 데이터를 시각화 해주는 웹 서비스',
            workList: [
              '· 프론트엔드 개발',
              '· 신규 개발 제품 Gateway에 대한 관련 기능 및 UI 변경 사항 반영',
              '· Flask babel을 이용하여 SSR 렌더링을 통한 이용 약관에 관련된 페이지의 다국어 message.pot로 적용',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2020.08 ~ 2020.09'
          },
          {
            img: 'img/portfolio/img-iaq-admin.PNG',
            name: 'BuildThing IAQ Admin 앱 (자사 서비스)',
            skill: 'Quasar Framework, Cordova, Vue.js, JavaScript, Stylus, Open Api, Kendo UI',
            intro: '신규 개발 제품 IAQ(실내 공기질 측정), Gateway를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결, 공간 및 기기 관리를 통해 IAQ, Gateway 등록 관리 및 실내 공기질 수치 정보 제공해주며 공기질 상태에 따라 WebSocket을 통한 푸시 알림 제공',
            workList: [
              '· 프론트엔드 개발',
              '· Quasar Framework에서 제공해주는 Cordova를 통해 하이브리드 앱 개발 환경 셋업',
              '· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발',
              '· Android 부분을 담당하여 개발 및 구글 플레이 스토어 배포',
              '· 자사에서 개발한 SDK와 캐러셀 등 공용 컴포넌트를 통해 담당 페이지 구현 및 시각화',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2020.08 ~ 2020.08'
          },
          {
            img: 'img/portfolio/img-buildthing-admin.PNG',
            name: 'BuildThing Admin 앱 (자사 서비스)',
            skill: 'Quasar Framework, Cordova, Electron, Vue.js, JavaScript, Stylus, Kendo UI',
            intro: '자사 개발 제품 BuildThing Beacon(실내 공기질 측정)과 BuildThing Gateway를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 영역 마다 설치되어있는 비콘과 게이트웨이부터 받아온 데이터를 기반으로 실시간 모니터링 및 웹 소켓을 통한 푸시 알람으로 영역을 관리하며 데이터를 시각화 해주는 앱',
            workList: [
              '· 프론트엔드 개발',
              '· 신규 개발 제품 Gateway에 대한 관련 기능 및 UI 변경 사항 반영',
              '· Android와 Window 앱 담당 및 구글 플레이 스토어, 마이크로스토어 배포',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2020.08 ~ 2020.08'
          },
          {
            img: 'img/portfolio/img-iaq-scan.PNG',
            name: 'BuildThing IAQ 앱 (자사 서비스)',
            skill: 'Quasar Framework, Cordova, Vue.js, JavaScript, Stylus, Open Api, Kendo UI',
            intro: '신규 개발 제품 IAQ(실내 공기질 측정)를 통해 주변 IAQ 기기를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 현재 위치 한 건물 내의 실내 공기질 수치 정보 제공 및 실내 공기질 요소별 등급과 환기 조치 가이드 제공',
            workList: [
              '· 프론트엔드 개발',
              '· Quasar Framework에서 제공해주는 Cordova를 통해 하이브리드 앱 개발 환경 셋업',
              '· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발',
              '· Android 부분을 담당하여 개발 및 구글 플레이 스토어 배포',
              '· 자사에서 개발한 SDK와 각 종 UI 컴포넌트를 통해 담당 페이지 기능 구현 및 시각화',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2020.08 ~ 2020.08'
          },
          {
            img: 'img/portfolio/img-smart-building.jpg',
            name: 'B.IoT v1.3 (스마트 빌딩 솔루션)',
            skill: 'Spring boot Framework, MVVM pattern, jQuery, JavaScript, GridStack.js, i18n.js, HTML5, CSS3, Kendo UI',
            intro: '건물 관리 자동화와 건물 에너지 절감을 위한 솔루션의 개발을 위해 진행 되었고 Web 화면을 통해 특정 건물에 설치된 각 종 기기들을 관리하고 실시간으로 모니터링 및 원격 제어하며, 해당 기기들의 이력과 통계 데이터를 확인할 수 있습니다. 또한 실시간 알람을 통해 건물 내 주요 이슈 현황을 파악',
            workList: [
              '· 프론트엔드 유지보수 및 개발',
              '· 담당 페이지에 대한 각 종 컴포넌트를 통한 신규 및 추가 기능 개발',
              '· 담당 페이지에 대한 개선 사항 반영 및 현장 이슈 대응',
              '· 유지보수 및 Chrom inspector를 통한 성능 개선',
              '· 고객사의 디자인 가이드 라인을 제공 받아 디자인 반영',
            ],
            manageSource: 'Git(SourceTree)',
            period: '2020.03 ~ 2020.10'
          },
          {
            img: 'img/portfolio/img-buildit-homepage.PNG',
            name: '자사 홈페이지',
            skill: 'Quasar Framework, Vue.js, TypeScript, JavaScript, i18n.js, Stylus',
            intro: '20년도 자사 홈페이지 리뉴얼',
            workList: [
              '· 프론트엔드 개발',
              '· Vue.js만 사용하던 이전과 다르게 TypeScript를 함께 사용 및 환경 셋업',
              '· Quasar Framework에서 지원해주는 컴포넌트 및 그리드 레이아웃을 통해 반응형 개선',
              '· 이전 홈페이지에서 신규 페이지 및 변경 된 페이지 개발',
              '· 공용 컴포넌트 개발',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2020.02 ~ 2020.03'
          },
          {
            img: 'img/portfolio/img-smart-building.jpg',
            name: 'B.IoT v1.2 (스마트 빌딩 솔루션)',
            skill: 'Spring boot Framework, MVVM pattern, jQuery, JavaScript, GridStack.js, i18n.js, HTML5, CSS3, Kendo UI',
            intro: '신규 개발 제품 IAQ (실내 공기질 측정), Gateway를 통해 공간 및 기기 관리를 통해 IAQ, Gateway 등록 관리 및 실내 공기질 수치 정보 제공',
            workList: [
              '· 프론트엔드 유지보수 및 개발',
              '· 인수인계 받은 담당 페이지에 대한 개선 사항 개발',
              '· 담당 페이지 유지보수 및 Chrom inspector를 통한 성능 개선',
              '· 고객사의 디자인 가이드 라인을 제공 받아 디자인 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2019.05 ~ 2020.02'
          },
          {
            img: 'img/portfolio/img-security.jpg',
            name: 'A4S (보안 정보 모니터링 솔루션)',
            skill: 'Spring boot Framework, Vue.js, jQuery, JavaScript, GridStack.js, Stylus, Kendo UI',
            intro: '연구 과제로 사용자 권한 별, 툴 별, 과제 별, 조직 별의 보안 관련 정보의 조회가 가능하며 각 종 차트를 통한 보안 관련 정보 시각화 및 사용자가 직접 추가/편집이 가능한 사용자 정의형 대시보드 와 사용자 및 권한 관리가 주요 기능인 웹 서비스',
            workList: [
              '· 프론트엔드 개발',
              '· Kendo UI에서 제공해주는 차트 컴포넌트를 통해 데이터 시각화',
              '· 요구사항에 맞게 각 종 컴포넌트를 사용하여 각 페이지의 기능 구현',
              '· Gridstack.js를 사용하여 대시보드 카드 및 추가, 편집, 삭제 구현',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2019.05 ~ 2019.10'
          },
          {
            img: 'img/portfolio/img-buildthing-cloud.PNG',
            name: 'BuildThing Cloud (자사 서비스)',
            skill: 'Quasar Framework, Vue.js, JavaScript, Stylus, Kendo UI',
            intro: '자사 개발 제품 BuildThing Beacon(실내 공기질 측정)으로 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 영역 마다 설치되어있는 비콘으로부터 받아온 데이터를 기반으로 실시간 모니터링 및 웹 소켓을 통한 푸시 알람으로 영역을 관리하며 데이터를 시각화 해주는 서비스',
            workList: [
              '· 프론트엔드 개발',
              '· Chart.js를 Kendo UI의 차트로 변경 수행 및 추가 된 센서 데이터 시각화 구현',
              '· 리뉴얼 한 대시보드 페이지 외에 담당 페이지를 Kendo UI에서 제공하는 컴포넌트 및 기존에 구현 되어있는 공용 컴포넌트를 통해 요구사항에 맞게 기능 구현',
              '· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영'
            ],
            manageSource: 'Git(SourceTree)',
            period: '2019.05 ~ 2019.05'
          },
          {
            img: 'img/portfolio/img-factory.jpg',
            name: 'MES 시스템 2.0',
            skill: 'Spring Framework, MVC pattern, JavaScript, HTML, CSS3, Oracle',
            intro: 'MES 시스템 유지보수 및 운영을 통해 현장 이슈 대응과 업무 Flow 개선으로 생산성 향상과 편의 제공',
            workList: [
              '· 시스템 운영 및 유지보수',
              '· MES시스템(포항 / 광양)의 구내운송 부분의 운송장비 관리 및 모니터링 그리고 계량 부분을 담당',
              '· 업무 Flow에 대한 개선 안에 대해 개발 진행',
              '· 제철소 특성으로 연중 무휴로 가동되기 때문에 야간/주말에 발생하는 현장의 전산 이슈에 대해 다른 팀원들과 함께 협업을 통하여 대응',
              '· 코드 수정 및 신규 기능으로 인해 추가 된 코드를 종합하여 운영 서버에서 테스트 이후 정기 이행일에 맞추어 가동계 서버로 자원 이행'
            ],
            manageSource: 'Serena Demension',
            period: '2018.04 ~ 2018.12'
          },
          {
            img: 'img/portfolio/img-swc-web.PNG',
            name: 'SWC 웹 (자사 서비스)',
            skill: 'Spring Framework, MVC pattern, Java, Mybatis, Oracle, jQuery, JavaScript, HTML5, CSS3',
            intro: '입주민 및 외부인이 웹페이지를 통하여 단지 내의 시설 이용 활성화 및 편의 제공해주는 아파트 커뮤니티 서비스',
            workList: [
              '· 프론트엔드 개발',
              '· 아파트 커뮤니티 웹 사이트와 키오스크 개발을 진행하였으며 주 업무로 웹 사이트의 시스템 관리 부분의 화면과 키오스크의 도서관 좌석 배정, 골프장 타석 배정, 게스트룸 객실 관리 부분의 페이지를 담당',
              '· 쿼리문 작성과 공용 컴포넌트를 통해 각 페이지의 요구사항에 맞게 데이터를 가공하여 기능 구현',
              '· 퍼블리셔와의 협업으로 제공해준 기본 Layout 내에서 디자인 가이드라인 반영'
            ],
            manageSource: 'SVN',
            period: '2017.11 ~ 2018.03'
          },
          {
            img: 'img/portfolio/img-swc-web.PNG',
            name: 'SWC 키오스크 (자사 서비스)',
            skill: 'Spring Framework, MVC pattern, Java, Mybatis, Oracle, jQuery, JavaScript, HTML5, CSS3',
            intro: '입주민 및 외부인이 키오스크를 통하여 단지 내의 시설 이용 활성화 및 편의 제공해주는 아파트 커뮤니티 서비스',
            workList: [
              '· 프론트엔드 개발',
              '· 아파트 커뮤니티 웹 사이트와 키오스크 개발을 진행하였으며 주 업무로 웹 사이트의 시스템 관리 부분의 화면과 키오스크의 도서관 좌석 배정, 골프장 타석 배정, 게스트룸 객실 관리 부분의 페이지를 담당',
              '· 쿼리문 작성과 공용 컴포넌트를 통해 각 페이지의 요구사항에 맞게 데이터를 가공하여 기능 구현',
              '· 퍼블리셔와의 협업으로 제공해준 기본 Layout 내에서 디자인 가이드라인 반영'
            ],
            manageSource: 'SVN',
            period: '2018.02 ~ 2018.03'
          },
          {
            img: 'img/portfolio/img-erp.jpg',
            name: '통합 IT 시스템 구축',
            skill: 'X-PLATFORM, JavaScript, Oracle',
            intro: 'ERP 시스템 구축으로 보다 효율적인 업무 진행과 생산성 향상',
            workList: [
              '· 프론트엔드 개발',
              '· 투비소프트의 X-PLATFORM 을 사용하여 ERP시스템의 구매 부분을 담당',
              '· X-PLATFORM에서 제공해주는 컴포넌트를 통해 가이드 라인 반영',
              '· 필요한 데이터에 맞게 쿼리문 작성과 플랫폼에서 제공해주는 컴포넌트를 통해 요구사항에 맞게 기능 구현'
            ],
            manageSource: 'SVN',
            period: '2017.06 ~ 2017.10'
          },
          {
            img: 'img/portfolio/img-swc-web.PNG',
            name: 'SWC Wall-Pad (자사 서비스)',
            skill: 'Spring Framework, MVC pattern, Java, Mybatis, Oracle, jQuery, JavaScript, HTML5, CSS3',
            intro: '입주민이 실내에서 Wall-Pad를 통하여 단지 내의 시설 예약 및 관리비 정산 등의 편의를 제공해주는 아파트 커뮤니티 서비스',
            workList: [
              '· 프론트엔드 개발',
              '· 아파트 커뮤니티 웹 사이트와 키오스크 개발을 진행하였으며 주 업무로 웹 사이트의 시스템 관리 부분의 화면과 키오스크의 도서관 좌석 배정, 골프장 타석 배정, 게스트룸 객실 관리 부분의 페이지를 담당',
              '· 쿼리문 작성과 공용 컴포넌트를 통해 각 페이지의 요구사항에 맞게 데이터를 가공하여 기능 구현',
              '· 퍼블리셔와의 협업으로 제공해준 기본 Layout 내에서 디자인 가이드라인 반영'
            ],
            manageSource: 'SVN',
            period: '2017.04 ~ 2017.05'
          }
        ]
      };
    }
  };
</script>
<style>
.el-table.table-dark{
  background-color: #172b4d;
  color: #f8f9fe;
}

.el-table.table-dark th,
.el-table.table-dark tr{
  background-color: #172b4d;
}

.el-table.table-dark td,
.el-table.table-dark th.is-leaf{
  border-bottom: none;
}
.portfolio-wrapper .portfolio-background {
  background: linear-gradient(87deg, #5eb3e482 0, #2d50ce 100%) !important;
}

.portfolio-wrapper .detail-card-block {
  margin-top: 6rem;
}

.portfolio-wrapper .detail-card-block .content-title {
  font-weight: 600;
}

.portfolio-wrapper .detail-card-block .used-skill,
.portfolio-wrapper .detail-card-block .intro,
.portfolio-wrapper .detail-card-block .my-work,
.portfolio-wrapper .detail-card-block .manage-source,
.portfolio-wrapper .detail-card-block .period {
  font-weight: 400;
}
.portfolio-wrapper .card .font-weight-bold {
  font-size: 16px;
}
.portfolio-wrapper .card .block {
  display: block;
}
.portfolio-wrapper .card.military-period .font-weight-bold {
  font-size: 13px;
}
.portfolio-wrapper .card.phone-number .font-weight-bold {
  font-size: 13px;
}
</style>
