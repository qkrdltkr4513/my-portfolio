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

    <el-table class="table-responsive table project-history"
              :data="tableData"
              header-row-class-name="thead-light">
      <el-table-column label="프로젝트 명"
                       min-width="120px"
                       prop="page">
        <template v-slot="{row}">
          <div class="font-weight-600 project-history-name">{{row.page}}</div>
        </template>
      </el-table-column>
      <el-table-column label="프로젝트 기간"
                       min-width="100px"
                       prop="period">
      </el-table-column>
      <el-table-column label="사용 기술"
                       min-width="130px"
                       prop="skill">
       <template v-slot="{row}">
         <div class="project-history-skill">{{row.skill}}</div>
       </template>
      </el-table-column>
      <el-table-column label="진행 상태"
                       min-width="130px"
                       prop="status">
      </el-table-column>
    </el-table>
  </b-card>
</template>
<script>
  import { Table, TableColumn, DropdownMenu, DropdownItem, Dropdown} from 'element-ui'
  export default {
    name: 'page-visits-table',
    components: {
      [Table.name]: Table,
      [TableColumn.name]: TableColumn,
      [Dropdown.name]: Dropdown,
      [DropdownItem.name]: DropdownItem,
      [DropdownMenu.name]: DropdownMenu,
    },
    data() {
      return {
        tableData: [
          {
            page: 'M닷컴 (자사 서비스)',
            period: '21.03 ~ 21.03',
            skill: 'React.js, Redux, javascript, ES6 etc..',
            status: '개발 진행중'
          },
          {
            page: 'One Click (자사 서비스)',
            period: '21.02 ~ 21.03',
            skill: 'Vue.js, javascript, Stylus, ES6 etc..',
            status: '개발 완료'
          },
          {
            page: '스마트폰샵 (자사 서비스) 유지보수',
            period: '21.01 ~ 21.03',
            skill: 'React.js, javascript, ES6, Kakao Pay API etc..',
            status: '추가 개발 진행중'
          },
          {
            page: '핀다이렉트샵 (프로모션 홈페이지)',
            period: '21.01 ~ 21.01',
            skill: 'GatsBy, javascript, HTML5 CSS3 etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing LoadCell Server',
            period: '20.11 ~ 20.11',
            skill: 'Quasar Framework, Vue.js, Stylus etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing LoadCell Admin 앱',
            period: '20.11 ~ 20.11',
            skill: 'Quasar Framework, Cordova, Vue.js etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing LoadCell 앱',
            period: '20.11 ~ 20.11',
            skill: 'Quasar Framework, Cordova, Vue.js etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing IAQ Cloud',
            period: '20.09 ~ 20.10',
            skill: 'Quasar Framework, Vue.js, Stylus etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing Cloud',
            period: '20.08 ~ 20.09',
            skill: 'Quasar Framework, Vue.js, Stylus etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing IAQ Admin 앱',
            period: '20.08 ~ 20.09',
            skill: 'Quasar Framework, Cordova, Vue.js etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing Admin 앱',
            period: '20.08 ~ 20.08',
            skill: 'Quasar Framework, Cordova, Electron etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing Cloud',
            period: '20.08 ~ 20.09',
            skill: 'Quasar Framework, Vue.js, Stylus etc..',
            status: '개발 완료'
          },
          {
            page: 'B.IoT v1.3',
            period: '20.03 ~ 20.10',
            skill: 'Spring boot Framework, jQuery, JavaScript etc..',
            status: '개발, 유지보수 완료'
          },
          {
            page: '20년 홈페이지',
            period: '20.02 ~ 20.03',
            skill: 'Quasar Framework, Vue.js, TypeScript etc..',
            status: '개발 완료'
          },
          {
            page: 'B.IoT v1.2',
            period: '19.05 ~ 20.02',
            skill: 'Spring boot Framework, jQuery, JavaScript etc..',
            status: '개발, 유지보수 완료'
          },
          {
            page: 'A4S',
            period: '19.05 ~ 19.10',
            skill: 'Spring boot Framework, Vue.js, jQuery etc..',
            status: '개발 완료'
          },
          {
            page: 'BuildThing Cloud',
            period: '19.05 ~ 19.05',
            skill: 'Quasar Framework, Vue.js, JavaScript etc..',
            status: '개발 완료'
          },
          {
            page: 'MES 2.0',
            period: '18.04 ~ 18.12',
            skill: 'Spring Framework, JavaScript, HTML etc..',
            status: '유지보수 및 운영 중 퇴사'
          },
          {
            page: 'SWC 웹',
            period: '17.11 ~ 18.03',
            skill: 'Spring Framework, jQuery, JavaScript etc..',
            status: '개발 완료'
          },
          {
            page: 'SWC 키오스크',
            period: '18.02 ~ 18.03',
            skill: 'Spring Framework, jQuery, JavaScript etc..',
            status: '개발 완료'
          },
          {
            page: '통합 IT 시스템 구축',
            period: '19.05 ~ 19.05',
            skill: 'X-PLATFORM, JavaScript, Oracle',
            status: '개발 완료'
          },
          {
            page: 'SWC Wall-Pad',
            period: '17.04 ~ 17.05',
            skill: 'Spring Framework, jQuery, JavaScript etc..',
            status: '개발 완료'
          },
        ]
      }
    }
  }
</script>
<style>
.project-history {
  max-height: 500px;
  overflow: auto;
}

@media screen and (max-width: 500px) {
  .table.project-history .el-table__body {
    width: 440px !important;
    table-layout: unset
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
