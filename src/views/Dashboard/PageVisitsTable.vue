<template>
  <b-card body-class="p-0" header-class="border-0">
    <template v-slot:header>
      <b-row align-v="center">
        <b-col>
          <h3 class="mb-0">프로젝트 경험</h3>
        </b-col>
        <b-col class="text-right">
          <a href="#/portfolio" class="btn btn-sm btn-primary">See all</a>
        </b-col>
      </b-row>
    </template>

    <el-table
      class="table-responsive table project-history"
      :data="tableData"
      header-row-class-name="thead-light"
    >
      <el-table-column label="프로젝트 명" min-width="120px" prop="page">
        <template v-slot="{ row }">
          <div class="font-weight-600 project-history-name">{{ row.page }}</div>
        </template>
      </el-table-column>
      <el-table-column label="프로젝트 기간" min-width="110px" prop="period">
      </el-table-column>
      <el-table-column label="사용 기술" min-width="140px" prop="skill">
        <template v-slot="{ row }">
          <div class="project-history-skill">{{ row.skill }}</div>
        </template>
      </el-table-column>
      <el-table-column label="담당 업무" min-width="110px" prop="position">
      </el-table-column>
    </el-table>
  </b-card>
</template>
<script>
import {
  Table,
  TableColumn,
  DropdownMenu,
  DropdownItem,
  Dropdown
} from "element-ui";
export default {
  name: "page-visits-table",
  components: {
    [Table.name]: Table,
    [TableColumn.name]: TableColumn,
    [Dropdown.name]: Dropdown,
    [DropdownItem.name]: DropdownItem,
    [DropdownMenu.name]: DropdownMenu
  },
  data() {
    return {
      tableData: [
        {
          page: "ITSM 통합관리자 (전사 서비스)",
          period: "24.07 ~ 진행중",
          skill: "Next.js, Typescript, Turbo Repo, Module Federation..",
          position: "프론트엔드 개발"
        },
        {
          page: "NCI (전사 서비스)",
          period: "24.03 ~ 23.07",
          skill: "Next.js, Typescript, Turbo Repo, Recoil..",
          position: "개발 및 유지보수"
        },
        {
          page: "NSD 앱 (전사 서비스)",
          period: "23.04 ~ 23.11",
          skill: "React-Native, Expo, Typescript, Recoil..",
          position: "개발 및 유지보수"
        },
        {
          page: "NSD (전사 서비스)",
          period: "23.01 ~ 23.11",
          skill: "React.js, Typescript, Recoil, React-Query..",
          position: "개발 및 유지보수"
        },
        {
          page: "ITSM 디자인 시스템",
          period: "22.07 ~ 22.12",
          skill: "React.js, Typescript, Storybook, Emotion..",
          position: "프론트엔드 개발"
        },
        {
          page: "핀다이렉트Z (자사몰)",
          period: "22.01 ~ 22.06",
          skill: "Next.js, Typescript, Recoil, React-query..",
          position: "프론트엔드 개발"
        },
        {
          page: "핀다이렉트샵 1.0 (자사몰)",
          period: "21.03 ~ 22.02",
          skill: "React.js, React-redux, React-apexchart, AWS S3..",
          position: "프론트엔드 개발"
        },
        {
          page: "One Click (자사 서비스)",
          period: "21.02 ~ 21.02",
          skill: "Vue.js, Vuex, Stylus",
          position: "프론트엔드 개발"
        },
        {
          page: "스마트폰샵 (자사 서비스)",
          period: "21.01 ~ 22.02",
          skill: "React.js, React-redux, Styled-compoments",
          position: "유지보수"
        },
        {
          page: "프로모션 홈페이지",
          period: "21.01 ~ 21.01",
          skill: "GatsBy, AWS S3, CSS3",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing LoadCell Server",
          period: "20.11 ~ 20.11",
          skill: "Quasar Framework, Vue.js, Stylus..",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing LoadCell Admin 앱",
          period: "20.11 ~ 20.11",
          skill: "Quasar Framework, Cordova, Vue.js..",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing LoadCell 앱",
          period: "20.11 ~ 20.11",
          skill: "Quasar Framework, Cordova, Vue.js..",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing IAQ Cloud",
          period: "20.09 ~ 20.10",
          skill: "Quasar Framework, Vue.js, Stylus..",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing Cloud",
          period: "20.08 ~ 20.09",
          skill: "Quasar Framework, Vue.js, Stylus..",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing IAQ Admin 앱",
          period: "20.08 ~ 20.09",
          skill: "Quasar Framework, Cordova, Vue.js..",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing Admin 앱",
          period: "20.08 ~ 20.08",
          skill: "Quasar Framework, Cordova, Electron..",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing Cloud",
          period: "20.08 ~ 20.09",
          skill: "Quasar Framework, Vue.js, Stylus..",
          position: "프론트엔드 개발"
        },
        {
          page: "B.IoT v1.3",
          period: "20.03 ~ 20.10",
          skill: "jQuery, CSS, Kendo UI, Gridstack.js..",
          position: "개발 및 유지보수"
        },
        {
          page: "20년 자사 홈페이지",
          period: "20.02 ~ 20.03",
          skill: "Quasar Framework, Vue.js, TypeScript..",
          position: "프론트엔드 개발"
        },
        {
          page: "B.IoT v1.2",
          period: "19.05 ~ 20.02",
          skill: "jQuery, CSS, Kendo UI, Gridstack.js",
          position: "개발 및 유지보수"
        },
        {
          page: "A4S",
          period: "19.05 ~ 19.10",
          skill: "Vue.js, Stylus, Kendo UI, Gridstack.js",
          position: "프론트엔드 개발"
        },
        {
          page: "BuildThing Cloud",
          period: "19.05 ~ 19.05",
          skill: "Quasar Framework, Vue.js, Kendo UI..",
          position: "프론트엔드 개발"
        },
        {
          page: "MES 2.0",
          period: "18.04 ~ 18.12",
          skill: "Spring Framework, JavaScript, HTML..",
          position: "유지보수 및 운영"
        },
        {
          page: "SWC 웹",
          period: "17.11 ~ 18.03",
          skill: "Spring Framework, jQuery, JavaScript..",
          position: "프론트엔드 개발"
        },
        {
          page: "SWC 키오스크",
          period: "18.02 ~ 18.03",
          skill: "Spring Framework, jQuery, JavaScript..",
          position: "프론트엔드 개발"
        },
        {
          page: "통합 IT 시스템 구축",
          period: "19.05 ~ 19.05",
          skill: "X-PLATFORM, Oracle",
          position: "시스템 개발"
        },
        {
          page: "SWC Wall-Pad",
          period: "17.04 ~ 17.05",
          skill: "Spring Framework, jQuery, JavaScript..",
          position: "프론트엔드 개발"
        }
      ]
    };
  }
};
</script>
<style>
.project-history {
  max-height: 560px;
  overflow: auto;
}

@media screen and (max-width: 500px) {
  .table.project-history .el-table__body {
    width: 440px !important;
    table-layout: unset;
  }

  .project-history-name {
    display: -webkit-box;
    /* max-width: 110px; */
    white-space: pre-wrap;
    text-overflow: ellipsis;
    /* overflow: hidden; */
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }
}
</style>
