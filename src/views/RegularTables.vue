<template>
  <div class="portfolio-wrapper">
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 portfolio-background">
      <!-- Card stats -->
      <b-row>
        <b-col xl="3" md="6">
          <stats-card
            title="개인정보"
            type="gradient-red"
            sub-title="박이삭"
            icon="ni ni-circle-08"
            class="mb-4"
          >
            <template slot="footer">
              <div class="first-line">
                <span class="text-success mr-2">나이:</span>
                <span class="text-nowrap mr-4">33세</span>
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
          <stats-card
            title="병역사항"
            type="gradient-orange"
            sub-title="2012.01 ~ 2013.10"
            icon="ni ni-user-run"
            class="mb-4 military-period"
          >
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
          <stats-card
            title="경력"
            type="gradient-green"
            sub-title="7년 2개월"
            icon="ni ni-laptop"
            class="mb-4"
          >
            <template slot="footer">
              <span class="text-success block mr-2">재직 여부</span>
              <span class="text-nowrap block">현재 재직중</span>
            </template>
          </stats-card>
        </b-col>
        <b-col xl="3" md="6">
          <stats-card
            title="연락처"
            type="gradient-info"
            sub-title="010-5629-0727"
            icon="ni ni-mobile-button"
            class="mb-4 phone-number"
          >
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
      <b-card
        v-for="(item, index) in projectList"
        :title="item.name"
        :img-src="item.img"
        img-alt="Image"
        img-top
        tag="article"
        style="margin: 0 auto; max-width: 40rem"
        class="mb-6"
      >
        <!-- <p class="title">사용기술</p> -->
        <span class="content-title">사용 기술</span>
        <b-card-text class="used-skill">{{ item.skill }}</b-card-text>

        <span class="content-title">프로젝트 목적</span>
        <b-card-text class="intro">{{ item.intro }}</b-card-text>

        <span class="content-title">담당 업무</span>
        <b-card-text>
          <p class="my-work" v-for="(work, workIndex) in item.workList">
            {{ work }}
          </p>
        </b-card-text>

        <span class="content-title">형상 관리</span>
        <b-card-text class="manage-source">{{ item.manageSource }}</b-card-text>

        <span class="content-title">프로젝트 기간</span>
        <b-card-text class="period">{{ item.period }}</b-card-text>

        <div v-if="!!item.url">
          <span class="content-title">
            <a :href="item.url" target="_blank">서비스 URL 및 소개</a>
          </span>
        </div>
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
import {
  Dropdown,
  DropdownItem,
  DropdownMenu,
  Table,
  TableColumn
} from "element-ui";
import projects from "./Tables/projects";
import users from "./Tables/users";
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
          img: "img/portfolio/img-security.jpg",
          name: "ITSM 통합관리자 (전사 서비스)",
          skill:
            "Next.js, Typescript, ITSM 컴포넌트, Turbo Repo, Recoil, React-Query, Emotion, Module Federation",
          intro:
            "NSD, NCI 서비스와 이후에 추가될 ITSM 서비스를 하나의 관리자 서비스로 통합하여 관리 기능을 제공하는 서비스",
          workList: [
            "· Module Federation 도입 검토 및 테스트",
            "· host app을 Next Federation으로 셋업",
            "· 각각의 기존 서비스 관리자 기능을 하나의 container로 분리 및 remote app 셋업",
            "· host app과 remote app 연결",
            "· 기획/디자인 리뷰 참여"
          ],
          manageSource: "Git(SourceTree)",
          period: "2024.07 ~ 진행중",
          url: null
        },
        {
          img: "img/portfolio/img-security.jpg",
          name: "NCI (전사 서비스)",
          skill:
            "Next.js, Typescript, ITSM 컴포넌트, Turbo Repo, Recoil, React-Query, Emotion, Web Socket, GA",
          intro:
            "게임, 인증, 거래소 등 회사에서 등록한 모든 서비스에 대한 장애를 옵스지니를 통해 구독하여 장애 발생시 서비스 담당자 및 해당 서비스를 구독한 사용자에게 SMS, 이메일, 푸시알림 채널을 통하여 장애를 전파하고 현재 장애 상태를 실시간으로 표시하는 서비스",
          workList: [
            "· 관리자 앱 프로젝트 셋업",
            "· 공용 Layout 컴포넌트 개발",
            "· 디자인 시스템으로 생성한 UI 컴포넌트로 프로젝트에 사용 될 공용 컴포넌트 개발",
            "· 로그인 페이지 개발",
            "· 관리자의 구독관리, 알림관리, 발송내역, 신고내역 페이지 개발",
            ". 디자이너와의 협업으로 Figma를 통하여 디자인 가이드 반영",
            "· 기획/디자인 리뷰 참여"
          ],
          manageSource: "Git(SourceTree)",
          period: "2024.03 ~ 2024.07",
          url: null
        },
        {
          img: "img/portfolio/img-security.jpg",
          name: "NSD 앱 (전사 서비스)",
          skill:
            "React-Native, Expo, Typescript, Recoil, React-query, Emotion, FCM, Azure, MS Intune",
          intro:
            "NSD 웹서비스를 관리자 기능을 제외하고 앱으로 생성한 것으로 사내망이 아닌 외부망에서도 업무 진행시 필요한 승인, 결재, 반려 등의 기능을 앱으로 제공하는 서비스",
          workList: [
            "· React Native 기술 검토",
            "· Expo를 통한 프로젝트 셋업 및 공용 컴포넌트 개발",
            "· WebView와 DeepLink를 통하여 로그인 개발",
            "· 결재, 처리, 요청, 상세 페이지 개발",
            "· FCM을 통한 push 알림 제공 및 알림 페이지 개발",
            "· 앱 내의 푸시알림 설정을 통한 디바이스 알림 설정 on/off 개발",
            "· Foreground, Background에 따른 상태관리",
            "· MS Teams 연동",
            "· AOS, IOS 빌드 및 사내포털에 앱 배포",
            "· 보안플랫폼 팀과의 협업으로 intune wrapping, MS Azure 앱 등록 및 MAM 정책 적용",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드 내용 반영",
            "· 기획/디자인 리뷰 참여",
            "· 서비스 오픈 이후 운영과 고도화 내용 반영 진행중"
          ],
          manageSource: "Git(SourceTree)",
          period: "2023.04 ~ 2023.11",
          url: null
        },
        {
          img: "img/portfolio/img-security.jpg",
          name: "NSD 웹(전사 서비스)",
          skill:
            "React.js, Typescript, ITSM 컴포넌트, Recoil, React-query, Emotion, React-flow, i18n, GA",
          intro:
            "전사 협업 서비스로 국내/외 법인, 조직, 부서, 사용자 간의 협업을 위한 태스크 관리 및 업무 진행에 있어 필요로하는 모든 요청서 신청, 승인, 결재 등을 제공하고 관리자 페이지를 통해 조직 및 사용자, 권한, 워크플로우, 요청서, 공통코드 등 관리 기능을 제공하는 서비스",
          workList: [
            "· 프로젝트 셋업",
            "· 디자인 시스템으로 생성한 UI 컴포넌트로 프로젝트에 사용 될 공용 컴포넌트 개발",
            "· React-flow 라이브러리를 통해 워크플로우 개발",
            "· Back-End 개발팀에 BFF API 도입 제안 및 도입",
            "· 워크플로우 조작 history를 쌓아 뒤로가기, 앞으로가기 초기화 기능 개발",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드 내용 반영",
            "· 기획/디자인 리뷰 참여",
            "· 서비스 오픈 이후 운영과 고도화 내용 반영 진행중"
          ],
          manageSource: "Git(SourceTree)",
          period: "2023.01 ~ 2023.11",
          url: null
        },

        {
          img: "img/portfolio/img-security.jpg",
          name: "ITSM 디자인 시스템",
          skill: "React.js, Typescript, Storybook, Emotion, Rollup, Nexus",
          intro:
            "공용 UI 컴포넌트 생성으로 기획, 디자인 직군과의 원활한 커뮤니케이션과 앞으로 진행 될 ITSM 서비스에 사용할 공용 UI 컴포넌트를 생성하여 제공",
          workList: [
            "· 디자인 시스템에 있는 기능 명세와 디자인 가이드를 제플린을 통해 ITSM 서비스에서 사용 될 UI 컴포넌트 개발",
            "· 디자인 가이드에 명시된 typography, color, 공용으로 사용 될 Themes 셋업",
            "· Rollup을 통해 사내 private 저장소인 Nexus에 업로드",
            "· 팀 내 Jira 태스크 관리 및 Naming 컨벤션, Git PR, Git Flow, 리뷰 도입",
            "· 디자인 검수 대응"
          ],
          manageSource: "Git(SourceTree)",
          period: "2022.07 ~ 2022.12",
          url: null
        },

        {
          img: "img/portfolio/img-pindirectshop2.0.png",
          name: "핀다이렉트Z(자사몰)",
          skill:
            "Next.js, React.js, Typescript, React-query, Recoil, ES6, AWS S3, Emotion, Framer-motion",
          intro:
            "현재 운영중인 핀다이렉트샵 1.0을 리뉴얼하고 보다 더 편리한 MVNO 주문 서비스 및 이벤트, 프로모션 제공",
          workList: [
            "· 개편 된 서비스 및 리뉴얼 된 디자인에 필요한 공용 컴포넌트 개발",
            "· 유심 주문 서비스 개발",
            "· 주문 배송 관리 및 마이페이지 개발",
            "· 실시간 데이터 사용량, 부가서비스 가입/해지, 요금제 변경 개발",
            "· KCP를 이용한 결제 연동",
            ". 1.0에서 판매 중이던 5G(MNO), 중고폰 서비스를 걷어내고 유심 위주의 MVNO 서비스 제공",
            ". 디자인 팀에서 요구하는 애니메이션을 Framer 및 CSS로 대응",
            ". 디자인 팀과의 협업으로 Figma를 통해 디자인 가이드 내용 반영",
            "· 기획/디자인 리뷰 참여"
          ],
          manageSource: "Git(SourceTree)",
          period: "2022.01 ~ 2022.06",
          url: "https://pindirectshop.com"
        },
        {
          img: "img/portfolio/img-pindirectshop-home.png",
          name: "핀다이렉트샵 1.0(자사몰)",
          skill:
            "React.js, React-redux, javascript, ES6, React-apexchart, AWS S3, Styled-components",
          intro:
            "기존 스마트폰샵과 다르게 카카오톡 앱을 통해 휴대폰을 구매하는 것이 아닌 독립적인 채널 확보와 5G / 중고폰 / 중고폰 / 유심 등의 MNO, MVNO 주문과 주문부터 셀프개통까지의 서비스를 제공하고 자사망을 이용하는 고객을 관리하며 각 종 이벤트 및 제휴프로그램, 프로모션 제공",
          workList: [
            "· 신규 기능에 필요한 공용 컴포넌트 개발",
            "· 중고폰, 중고폰 + 유심, 유심 주문 서비스 개발",
            "· 마이페이지 개발",
            "· 주문 배송 관리",
            ". 자사 망을 이용하는 고객 한에 사용 중인 요금제, 부가서비스 표시 및 Guage 차트를 이용한 잔여 데이터, 음성, 문자 시각화",
            ". NICE, 카카오페이 본인인증과 KCP를 이용한 결제 연동 (네이버 인증 추가 예정)",
            ". 라이브 서비스 이슈 대응",
            ". 마케팅 활용 목적으로 구글 애널리틱스 픽셀 연동",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영",
            "· 기획/디자인 리뷰 참여"
          ],
          manageSource: "Git(SourceTree)",
          period: "2021.03 ~ 2022.02",
          url: null
        },
        {
          img: "img/portfolio/img-one-click.png",
          name: "One Click(자사 서비스)",
          skill: "Vue.js, javascript, Stylus, ES6",
          intro:
            "고객과 상담원의 통화를 진행으로, 고객이 상담원의 안내에 따라 조금 더 쉽고 빠르게 상품 주문을 제공하는 모바일웹 서비스",
          workList: [
            "· 프로젝트 셋업 및 공용 컴포넌트 개발",
            "· 신규가입, 번호이동, 기기변경에 대한 주문 서비스 개발",
            "· NICE 본인 인증 (휴대폰/신용카드) 연동",
            ". KCP 결제 모듈 연동",
            "· 기획/디자인 리뷰 참여",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2021.02 ~ 2021.02",
          url: null
        },
        {
          img: "img/portfolio/img-smartphoneshop-home.png",
          name: "스마트폰샵(자사 서비스)",
          skill: "React.js, javascript, ES6, Styled-compoments",
          intro:
            "카카오페이에서 제공해주며 고객이 대리점 방문하지 않고 휴대폰(5G) 주문부터 개통까지 지원하는 서비스",
          workList: [
            "· 프론트엔드 개발 및 유지보수",
            "· 라이브 서비스 이슈 대응",
            "· 핀다이렉트샵(자사 서비스) 업데이트시 동기화 작업",
            "· 기획/디자인 리뷰 참여",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2021.01 ~ 2022.02",
          url: null
        },
        {
          img: "img/portfolio/img-pindirectshop.png",
          name: "프로모션 홈페이지",
          skill: "GatsBy, javascript, HTML5, CSS3",
          intro:
            "신규 스마트폰 출시에 따른 사전 예약 및 다양한 프로모션 그리고 이벤트 혜택등을 고객들에게 공지하고 안내하는 홈페이지",
          workList: [
            "· 신규 출시되는 스마트폰과 다양한 프로모션과 이벤트에 맞게 내용 수정",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2021.01 ~ 2021.01",
          url: null
        },
        {
          img: "img/portfolio/img-loadcell-map-view.png",
          name: "BuildThing Loadcell Server (자사 서비스)",
          skill:
            "Quasar Framework, Vue.js, jQuery, JavaScript, Stylus, Flask babel, GridStack.js, Open Api, Kendo UI",
          intro:
            "신규 개발 제품 Loadcell(하중 압력 측정)의 데이터를 Gateway로 부터 수신 받아 SDK를 통하여 스트레인게이지 변화 값을 통해 하중 값으로 변환하여 현재 하중이 얼마나 되는지 차트 및 mapVIew로 모니터링 서비스 제공해주며 하중 상태에 따라 WebSocket을 통한 푸시 알림 제공",
          workList: [
            "· 프론트엔드 개발",
            "· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발",
            "· 맵뷰에 표시되는 Loadcell 아이콘 클릭시 현재 하중에 대한 데이터를 plotly.js를 사용하여 3D 차트 표시",
            "· 각 종 UI 컴포넌트를 통해 담당 페이지 기능 구현 및 시각화",
            "· PG사 연동을 통한 결제 기능 구현 및 그룹 관리 기능 구현",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.11 ~ 2020.11",
          url: null
        },
        {
          img: "img/portfolio/img-security.jpg",
          name: "BuildThing Loadcell Admin 앱 (자사 서비스)",
          skill:
            "Quasar Framework, Vue.js, jQuery, JavaScript, Stylus, Flask babel, GridStack.js, Open Api, Kendo UI",
          intro:
            "신규 개발 제품 Loadcell(하중 압력 측정), Gateway를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 탄성체 내에 스트레인게이지를 부착하여 탄성체에 압력이 가해져 스트레인게이지 변화 값을 통해 하중 값으로 변환하여 현재 하중이 얼마나 되는지 모니터링 서비스 제공해주며 하중 상태에 따라 WebSocket을 통한 푸시 알림 제공",
          workList: [
            "· 프론트엔드 개발",
            "· Quasar Framework에서 제공해주는 Cordova를 통해 하이브리드 앱 개발 환경 셋업",
            "· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발",
            "· Android 부분을 담당하여 개발",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.11 ~ 2020.11",
          url: null
        },
        {
          img: "img/portfolio/img-security.jpg",
          name: "BuildThing Loadcell 앱 (자사 서비스)",
          skill: "Quasar Framework, Cordova, Vue.js, javascript, Stylus, ES6",
          intro:
            "신규 개발 제품 Loadcell(하중 압력 측정)을 통해 탄성체 내에 스트레인게이지를 부착하여 탄성체에 압력이 가해져 스트레인게이지 변화 값을 통해 하중 값으로 변환하여 현재 하중이 얼마나 되는지 모니터링 서비스 제공",
          workList: [
            "· 프론트엔드 개발",
            "· Quasar Framework에서 제공해주는 Cordova를 통해 하이브리드 앱 개발 환경 셋업",
            "· Quasar Framework와 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발",
            "· Android 부분을 담당하여 개발",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.10 ~ 2020.11",
          url: null
        },
        {
          img: "img/portfolio/img-iaq-cloud-dashboard.PNG",
          name: "BuildThing IAQ Cloud (자사 서비스)",
          skill:
            "Quasar Framework, Vue.js, jQuery, JavaScript, Stylus, Flask babel, GridStack.js, leaflet.js, Open Api, Kendo UI",
          intro:
            "신규 개발 제품 IAQ (실내 공기질 측정), Gateway를 통해 공간 및 기기 관리를 통해 IAQ, Gateway 등록 관리 및 실내 공기질 수치 정보 제공",
          workList: [
            "· 프론트엔드 개발",
            "· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발",
            "· Gridstack.js를 사용하여 대시보드 카드 생성, 편집(위치 이동), 삭제 기능 구현",
            "· 자사에서 개발한 SDK와 각 종 UI 컴포넌트를 통해 담당 페이지 기능 구현 및 시각화",
            "· PG사 연동을 통한 결제 기능 구현 및 그룹 관리 기능 구현",
            "· Flask babel을 이용하여 SSR 렌더링을 통한 이용 약관에 관련된 페이지의 다국어 message.pot로 적용",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.08 ~ 2020.09",
          url: "https://www.youtube.com/watch?v=YdbAktMYipU&t=82s"
        },
        {
          img: "img/portfolio/img-iaq-admin.PNG",
          name: "BuildThing IAQ Admin 앱 (자사 서비스)",
          skill:
            "Quasar Framework, Cordova, Vue.js, JavaScript, Stylus, Open Api, Kendo UI",
          intro:
            "신규 개발 제품 IAQ(실내 공기질 측정), Gateway를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결, 공간 및 기기 관리를 통해 IAQ, Gateway 등록 관리 및 실내 공기질 수치 정보 제공해주며 공기질 상태에 따라 WebSocket을 통한 푸시 알림 제공",
          workList: [
            "· 프론트엔드 개발",
            "· Quasar Framework에서 제공해주는 Cordova를 통해 하이브리드 앱 개발 환경 셋업",
            "· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발",
            "· Android 부분을 담당하여 개발 및 구글 플레이 스토어 배포",
            "· 자사에서 개발한 SDK와 캐러셀 등 공용 컴포넌트를 통해 담당 페이지 구현 및 시각화",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.08 ~ 2020.08",
          url:
            "https://play.google.com/store/apps/details?id=kr.buildit.buildthing.airquality"
        },
        {
          img: "img/portfolio/img-buildthing-admin.PNG",
          name: "BuildThing Admin v1.1앱 (자사 서비스)",
          skill:
            "Quasar Framework, Cordova, Electron, Vue.js, JavaScript, Stylus, Kendo UI",
          intro:
            "자사 개발 제품 BuildThing Beacon(실내 공기질 측정)과 BuildThing Gateway를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 영역 마다 설치되어있는 비콘과 게이트웨이부터 받아온 데이터를 기반으로 실시간 모니터링 및 웹 소켓을 통한 푸시 알람으로 영역을 관리하며 데이터를 시각화 해주는 앱",
          workList: [
            "· 프론트엔드 개발",
            "· 신규 개발 제품 Gateway에 대한 관련 기능 및 UI 변경 사항 반영",
            "· Android와 Window 앱 담당 및 구글 플레이 스토어, 마이크로스토어 배포",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.08 ~ 2020.08",
          url:
            "https://play.google.com/store/apps/details?id=kr.buildit.buildthing.ble"
        },
        {
          img: "img/portfolio/img-iaq-scan.PNG",
          name: "BuildThing IAQ 앱 (자사 서비스)",
          skill:
            "Quasar Framework, Cordova, Vue.js, JavaScript, Stylus, Open Api, Kendo UI",
          intro:
            "신규 개발 제품 IAQ(실내 공기질 측정)를 통해 주변 IAQ 기기를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 현재 위치 한 건물 내의 실내 공기질 수치 정보 제공 및 실내 공기질 요소별 등급과 환기 조치 가이드 제공",
          workList: [
            "· 프론트엔드 개발",
            "· Quasar Framework에서 제공해주는 Cordova를 통해 하이브리드 앱 개발 환경 셋업",
            "· Quasar Framework와 Kendo UI에서 제공해주는 컴포넌트를 통해 공용 컴포넌트 개발",
            "· Android 부분을 담당하여 개발 및 구글 플레이 스토어 배포",
            "· 자사에서 개발한 SDK와 각 종 UI 컴포넌트를 통해 담당 페이지 기능 구현 및 시각화",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.08 ~ 2020.08",
          url:
            "https://play.google.com/store/apps/details?id=kr.buildit.buildthing.airquality.scan"
        },
        {
          img: "img/portfolio/img-buildthing-cloud-v1.PNG",
          name: "BuildThing Cloud v1.1(자사 서비스)",
          skill: "Quasar Framework, Vue.js, JavaScript, Stylus, Kendo UI",
          intro:
            "자사 개발 제품 BuildThing Beacon(실내 공기질 측정)과 BuildThing Gateway를 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 영역 마다 설치되어있는 비콘과 게이트웨이로부터 받아온 데이터를 기반으로 실시간 모니터링 및 웹 소켓을 통한 푸시 알람으로 영역을 관리하며 데이터를 시각화 해주는 웹 서비스",
          workList: [
            "· 프론트엔드 개발",
            "· 신규 개발 제품 Gateway에 대한 관련 기능 및 UI 변경 사항 반영",
            "· Flask babel을 이용하여 SSR 렌더링을 통한 이용 약관에 관련된 페이지의 다국어 message.pot로 적용",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2019.07 ~ 2019.08",
          url: null
        },
        {
          img: "img/portfolio/img-smart-building.jpg",
          name: "B.IoT v1.3 (스마트 빌딩 솔루션)",
          skill:
            "Spring boot Framework, MVVM pattern, jQuery, JavaScript, GridStack.js, i18n.js, HTML5, CSS3, Kendo UI",
          intro:
            "건물 관리 자동화와 건물 에너지 절감을 위한 솔루션의 개발을 위해 진행 되었고 Web 화면을 통해 특정 건물에 설치된 각 종 기기들을 관리하고 실시간으로 모니터링 및 원격 제어하며, 해당 기기들의 이력과 통계 데이터를 확인할 수 있습니다. 또한 실시간 알람을 통해 건물 내 주요 이슈 현황을 파악",
          workList: [
            "· 프론트엔드 유지보수 및 개발",
            "· 담당 페이지에 대한 각 종 컴포넌트를 통한 신규 및 추가 기능 개발",
            "· 담당 페이지에 대한 개선 사항 반영 및 현장 이슈 대응",
            "· 유지보수 및 Chrom inspector를 통한 성능 개선",
            "· 고객사의 디자인 가이드 라인을 제공 받아 디자인 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.03 ~ 2020.10",
          url:
            "https://www.samsung.com/sec/business/b-iot-solutions/b-iot-solution/"
        },
        {
          img: "img/portfolio/img-buildit-homepage.PNG",
          name: "자사 홈페이지",
          skill:
            "Quasar Framework, Vue.js, TypeScript, JavaScript, i18n.js, Stylus",
          intro: "20년도 자사 홈페이지 리뉴얼",
          workList: [
            "· 프론트엔드 개발",
            "· Vue.js만 사용하던 이전과 다르게 TypeScript를 함께 사용 및 환경 셋업",
            "· Quasar Framework에서 지원해주는 컴포넌트 및 그리드 레이아웃을 통해 반응형 개선",
            "· 이전 홈페이지에서 신규 페이지 및 변경 된 페이지 개발",
            "· 공용 컴포넌트 개발",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2020.02 ~ 2020.03",
          url: "https://buildit.kr"
        },
        {
          img: "img/portfolio/img-smart-building.jpg",
          name: "B.IoT v1.2 (스마트 빌딩 솔루션)",
          skill:
            "Spring boot Framework, MVVM pattern, jQuery, JavaScript, GridStack.js, i18n.js, HTML5, CSS3, Kendo UI",
          intro:
            "건물 관리 자동화와 건물 에너지 절감을 위한 솔루션의 개발을 위해 진행 되었고 Web 화면을 통해 특정 건물에 설치된 각 종 기기들을 관리하고 실시간으로 모니터링 및 원격 제어하며, 해당 기기들의 이력과 통계 데이터를 확인할 수 있습니다. 또한 실시간 알람을 통해 건물 내 주요 이슈 현황을 파악",
          workList: [
            "· 프론트엔드 유지보수 및 개발",
            "· 인수인계 받은 담당 페이지에 대한 개선 사항 개발",
            "· 담당 페이지 유지보수 및 Chrom inspector를 통한 성능 개선",
            "· 고객사의 디자인 가이드 라인을 제공 받아 디자인 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2019.05 ~ 2020.02",
          url:
            "https://www.samsung.com/sec/business/b-iot-solutions/b-iot-solution/"
        },
        {
          img: "img/portfolio/img-security.jpg",
          name: "A4S (보안 정보 모니터링 솔루션)",
          skill:
            "Spring boot Framework, Vue.js, jQuery, JavaScript, GridStack.js, Stylus, Kendo UI",
          intro:
            "삼성리서치 연구 과제로 사용자 권한 별, 툴 별, 과제 별, 조직 별의 보안 관련 정보의 조회가 가능하며 각 종 차트를 통한 보안 관련 정보 시각화 및 사용자가 직접 추가/편집이 가능한 사용자 정의형 대시보드와 사용자 및 권한 관리가 주요 기능인 웹 서비스",
          workList: [
            "· 프론트엔드 개발",
            "· Kendo UI에서 제공해주는 차트 컴포넌트를 통해 데이터 시각화",
            "· 요구사항에 맞게 각 종 컴포넌트를 사용하여 각 페이지의 기능 구현",
            "· Gridstack.js를 사용하여 대시보드 카드 및 추가, 편집, 삭제 구현",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2019.05 ~ 2019.10",
          url: null
        },
        {
          img: "img/portfolio/img-buildthing-cloud.PNG",
          name: "BuildThing Cloud v1.0(자사 서비스)",
          skill: "Quasar Framework, Vue.js, JavaScript, Stylus, Kendo UI",
          intro:
            "자사 개발 제품 BuildThing Beacon(실내 공기질 측정)으로 자사에서 개발한 SDK를 사용하여 Bluetooth로 연결을 통해 영역 마다 설치되어있는 비콘으로부터 받아온 데이터를 기반으로 실시간 모니터링 및 웹 소켓을 통한 푸시 알람으로 영역을 관리하며 데이터를 시각화 해주는 서비스",
          workList: [
            "· 프론트엔드 개발",
            "· Chart.js를 Kendo UI의 차트로 변경 수행 및 추가 된 센서 데이터 시각화 구현",
            "· 리뉴얼 한 대시보드 페이지 외에 담당 페이지를 Kendo UI에서 제공하는 컴포넌트 및 기존에 구현 되어있는 공용 컴포넌트를 통해 요구사항에 맞게 기능 구현",
            "· 디자이너와의 협업으로 제플린을 통해 디자인 가이드라인 내용 반영"
          ],
          manageSource: "Git(SourceTree)",
          period: "2019.05 ~ 2019.05",
          url: null
        },
        {
          img: "img/portfolio/img-factory.jpg",
          name: "MES 시스템 2.0",
          skill:
            "Spring Framework, MVC pattern, JavaScript, HTML, CSS3, Oracle",
          intro:
            "MES 시스템 유지보수 및 운영을 통해 현장 이슈 대응과 업무 Flow 개선으로 생산성 향상과 편의 제공",
          workList: [
            "· 시스템 운영 및 유지보수",
            "· MES시스템(포항 / 광양)의 구내운송 부분의 운송장비 관리 및 모니터링 그리고 계량 부분을 담당",
            "· 업무 Flow에 대한 개선 안에 대해 개발 진행",
            "· 제철소 특성으로 연중 무휴로 가동되기 때문에 야간/주말에 발생하는 현장의 전산 이슈에 대해 다른 팀원들과 함께 협업을 통하여 대응",
            "· 코드 수정 및 신규 기능으로 인해 추가 된 코드를 종합하여 운영 서버에서 테스트 이후 정기 이행일에 맞추어 가동계 서버로 자원 이행"
          ],
          manageSource: "Serena Demension",
          period: "2018.04 ~ 2018.12",
          url: null
        },
        {
          img: "img/portfolio/img-swc-web.PNG",
          name: "SWC 웹 (자사 서비스)",
          skill:
            "Spring Framework, MVC pattern, Java, Mybatis, Oracle, jQuery, JavaScript, HTML5, CSS3",
          intro:
            "입주민 및 외부인이 웹페이지를 통하여 단지 내의 시설 이용 활성화 및 편의 제공해주는 아파트 커뮤니티 서비스",
          workList: [
            "· 프론트엔드 개발",
            "· 아파트 커뮤니티 웹 사이트와 키오스크 개발을 진행하였으며 주 업무로 웹 사이트의 시스템 관리 부분의 화면과 키오스크의 도서관 좌석 배정, 골프장 타석 배정, 게스트룸 객실 관리 부분의 페이지를 담당",
            "· 쿼리문 작성과 공용 컴포넌트를 통해 각 페이지의 요구사항에 맞게 데이터를 가공하여 기능 구현",
            "· 퍼블리셔와의 협업으로 제공해준 기본 Layout 내에서 디자인 가이드라인 반영"
          ],
          manageSource: "SVN",
          period: "2017.11 ~ 2018.03",
          url: null
        },
        {
          img: "img/portfolio/img-swc-web.PNG",
          name: "SWC 키오스크 (자사 서비스)",
          skill:
            "Spring Framework, MVC pattern, Java, Mybatis, Oracle, jQuery, JavaScript, HTML5, CSS3",
          intro:
            "입주민 및 외부인이 키오스크를 통하여 단지 내의 시설 이용 활성화 및 편의 제공해주는 아파트 커뮤니티 서비스",
          workList: [
            "· 프론트엔드 개발",
            "· 아파트 커뮤니티 웹 사이트와 키오스크 개발을 진행하였으며 주 업무로 웹 사이트의 시스템 관리 부분의 화면과 키오스크의 도서관 좌석 배정, 골프장 타석 배정, 게스트룸 객실 관리 부분의 페이지를 담당",
            "· 쿼리문 작성과 공용 컴포넌트를 통해 각 페이지의 요구사항에 맞게 데이터를 가공하여 기능 구현",
            "· 퍼블리셔와의 협업으로 제공해준 기본 Layout 내에서 디자인 가이드라인 반영"
          ],
          manageSource: "SVN",
          period: "2018.02 ~ 2018.03",
          url: null
        },
        {
          img: "img/portfolio/img-erp.jpg",
          name: "통합 IT 시스템 구축",
          skill: "X-PLATFORM, JavaScript, Oracle",
          intro: "ERP 시스템 구축으로 보다 효율적인 업무 진행과 생산성 향상",
          workList: [
            "· 프론트엔드 개발",
            "· 투비소프트의 X-PLATFORM 을 사용하여 ERP시스템의 구매 부분을 담당",
            "· X-PLATFORM에서 제공해주는 컴포넌트를 통해 가이드 라인 반영",
            "· 필요한 데이터에 맞게 쿼리문 작성과 플랫폼에서 제공해주는 컴포넌트를 통해 요구사항에 맞게 기능 구현"
          ],
          manageSource: "SVN",
          period: "2017.06 ~ 2017.10",
          url: null
        },
        {
          img: "img/portfolio/img-swc-web.PNG",
          name: "SWC Wall-Pad (자사 서비스)",
          skill:
            "Spring Framework, MVC pattern, Java, Mybatis, Oracle, jQuery, JavaScript, HTML5, CSS3",
          intro:
            "입주민이 실내에서 Wall-Pad를 통하여 단지 내의 시설 예약 및 관리비 정산 등의 편의를 제공해주는 아파트 커뮤니티 서비스",
          workList: [
            "· 프론트엔드 개발",
            "· 아파트 커뮤니티 웹 사이트와 키오스크 개발을 진행하였으며 주 업무로 웹 사이트의 시스템 관리 부분의 화면과 키오스크의 도서관 좌석 배정, 골프장 타석 배정, 게스트룸 객실 관리 부분의 페이지를 담당",
            "· 쿼리문 작성과 공용 컴포넌트를 통해 각 페이지의 요구사항에 맞게 데이터를 가공하여 기능 구현",
            "· 퍼블리셔와의 협업으로 제공해준 기본 Layout 내에서 디자인 가이드라인 반영"
          ],
          manageSource: "SVN",
          period: "2017.04 ~ 2017.05",
          url: null
        }
      ]
    };
  }
};
</script>
<style>
.el-table.table-dark {
  background-color: #172b4d;
  color: #f8f9fe;
}

.el-table.table-dark th,
.el-table.table-dark tr {
  background-color: #172b4d;
}

.el-table.table-dark td,
.el-table.table-dark th.is-leaf {
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
