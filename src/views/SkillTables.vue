<template>
  <div class="skill-wrapper">
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 skill-background">
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
    <div class="main-content container-fluid">
      <stats-card
        title="핵심 역량"
        type="gradient-primary"
        icon="ni ni-check-bold"
        class="mt--6 mb-4"
      >
        <template slot="footer">
          <!-- <span class="text-success mr-2"><i class="fa fa-arrow-up"></i> 3.48%</span> -->
          <span
            style="display: block"
            class=""
            v-for="(ability, index) in coreAbility"
            >{{ ability }}</span
          >
        </template>
      </stats-card>
    </div>
    <b-container fluid class="mt-4 mb-4">
      <b-row>
        <b-col>
          <!-- <light-table/> -->
        </b-col>
      </b-row>
      <!-- <div class="mt-5"></div> -->
      <social-traffic-table></social-traffic-table>
    </b-container>
    <!-- <div class="container-fluid detail-card-block">
      <b-card
        v-for="(item, index) in skillList"
        :title="item.name"
        tag="article"
        style="margin: 0 auto; max-width: 28rem"
        class="mb-4"
      > -->
    <!-- <p class="title">사용기술</p> -->

    <!-- <span class="content-title">사용 기술명</span>
        <b-card-text class="skill-name">{{ item.skill }}</b-card-text>

        <span class="content-title">수준</span>
        <b-card-text class="skill-level">{{ item.level }}</b-card-text>

        <span class="content-title">상세 내용</span>
        <b-card-text>
          <p class="skill-desc" v-for="(desc, descIndex) in item.desc">
            {{ desc }}
          </p>
        </b-card-text> -->

    <!-- <b-card-body>
          This is some text within a card body.
        </b-card-body> -->

    <!-- <b-button href="javascript:;" variant="primary">Go somewhere</b-button> -->
    <!-- </b-card>
    </div> -->
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
import SocialTrafficTable from "./Dashboard/SocialTrafficTable";

export default {
  components: {
    LightTable,
    DarkTable,
    SocialTrafficTable,
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
      coreAbility: [
        "· HTML5 및 CSS3에 대한 이해 및 활용",
        "· CSS 전처리기(stylus) 사용 경험 보유",
        "· CSS In JS(Emotion, Styled-component) 사용 경험 보유",
        "· Javascript 및 jQuery 에 대한 이해 및 활용",
        "· Chrome Inspector 를 통해 성능 개선 경험 보유",
        "· SPA Framework에 대한 지식 보유 및 개발 경험(vue.js, react.js)",
        "· TypeScript 사용 경험 보유",
        "· UI 라이브러리를 통한 공용 차트 컴포넌트 개발 및 데이터 시각화 경험 보유(Kendo UI)",
        "· Quasar Framework를 통한 하이브리드 앱 개발 (Cordova, Electron) 및 스토어 배포 경험 보유",
        ". React-Native를 통한 크로스 플랫폼 앱 개발 (AOS, IOS 버전 관리) 및 사내포털 배포 경험 보유",
        "· 디자이너와의 협업을 통한 디자인 시스템 구축 경험 보유",
        "· 디자이너와의 적극적인 커뮤니케이션을 통한 협업 경험 보유(Figma, Zeplin)",
        "· 프로젝트 진행과정(A ~ Z) 및 진행 간에 발생한 트러블 슈팅을 Confluence를 통해 위키 작성",
        "· Jira를 통한 Task 관리 및 능동적인 업무 진행",
        "· 신기술 또는 새로운 환경에 대한 호기심과 탐구심 "
      ],
      skillList: [
        {
          skill: "Quasar Framework",
          level: "중",
          desc: [
            "· Quasar Framework를 기반으로 개발 환경 셋업(웹, cordova, electron)",
            "· Quasar Framework의 UI 컴포넌트를 커스텀을 통해 공용 컴포넌트 생성 및 활용 가능",
            "· Quasar Framework에서 지원해주는 cordova 및 electron을 통하여 하이브리드 앱 개발 경험 및 구글 스토어, 윈도우 스토어 배포 경험 보유"
          ]
        },
        {
          skill: "Vue.js",
          level: "중",
          desc: [
            "· Vue cli를 통한 개발 환경 셋업",
            "· 가상 DOM에 대한 이해",
            "· Vue.js의 LifeCycle과 디렉티브에 대한 이해 및 활용",
            "· 공용 컴포넌트 생성 및 컴포넌트 활용",
            "· Prerendering을 통한 SEO 경험 보유",
            "· Vuex를 통한 state 관리 및 활용"
          ]
        },
        {
          skill: "React.js",
          level: "중",
          desc: [
            ". Atomic 디자인 패턴 사용 경험",
            ". React.js의 LifeCycle 이해",
            "· 공용 컴포넌트 생성 및 컴포넌트 활용",
            "· Redux를 통한 state 관리",
            "· Redux-saga 미들웨어를 통한 비동기 통신 경험",
            "· recoil, react-query 공부 진행 중"
          ]
        },
        {
          skill: "jQuery",
          level: "중",
          desc: [
            "· jQuery에 대한 이해 및 활용",
            "· jQuery에서 지원해주는 API 활용과 선택자를 통한 요소 접근을 통하여 CSS 등 스타일링 및 데이터 가공 경험 다수 보유",
            "· MVC 및 MVVM 패턴 사용 경험 보유"
          ]
        },
        {
          skill: "TypeScript",
          level: "하",
          desc: [
            "· Vue.js와 TypeScript를 함께 사용한 경험 보유",
            "· TypeScript 문법 이해 및 사용 가능"
          ]
        },
        {
          skill: "JavaScript",
          level: "중",
          desc: [
            "· JavaScript에 대한 이해 및 활용 가능",
            "· JavaScript에서의 this에 대한 이해 및 활용 가능",
            "· Chrome Inspector를 통한 성능 개선 경험 보유",
            "· Open 라이브러리, Open Api 통한 개발 경험 보유"
          ]
        },
        {
          skill: "HTML5",
          level: "중",
          desc: [
            "· 웹 표준 및 웹 접근성을 준수한 시멘틱 마크업 생성 가능",
            "· 브라우저 렌더링 과정에 대한 이해"
          ]
        },
        {
          skill: "CSS3",
          level: "중",
          desc: [
            "· CSS3에 대한 이해 및 활용 가능",
            "· 디자이너의 가이드 및 요구사항에 맞게 스타일링 가능",
            "· 크로스 브라우저 이슈 대응 경험 보유",
            "· 반응형 스타일 경험 보유"
          ]
        },
        {
          skill: "Stylus",
          level: "중",
          desc: [
            "· 디자이너의 가이드 및 요구사항에 맞게 스타일링 가능",
            "· 웹/앱(WebView) 스타일 경험 보유",
            "· 크로스 브라우징 이슈 대응 경험 보유",
            "· 반응형 스타일 경험 보유"
          ]
        },
        {
          skill: "Kendo UI",
          level: "중",
          desc: [
            "· Kendo UI의 컴포넌트 사용 및 활용 가능",
            "· Kendo UI에서 지원해주는 UI 컴포넌트를 통하여 공용 컴포넌트 개발 및 활용 경험 보유"
          ]
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
.skill-wrapper .skill-background {
  background: linear-gradient(87deg, #5eb3e482 0, #2d50ce 100%) !important;
}
.skill-wrapper .card .font-weight-bold {
  font-size: 16px;
}
.skill-wrapper .card .block {
  display: block;
}
.skill-wrapper .card.military-period .font-weight-bold {
  font-size: 13px;
}
.skill-wrapper .card.phone-number .font-weight-bold {
  font-size: 13px;
}

.skill-wrapper .detail-card-block .content-title {
  font-weight: 600;
}

.skill-wrapper .detail-card-block .skill-name,
.skill-wrapper .detail-card-block .skill-level,
.skill-wrapper .detail-card-block .skill-desc {
  font-weight: 400;
}
.skill-wrapper .btn-sm.btn-primary {
  display: none;
}
</style>
