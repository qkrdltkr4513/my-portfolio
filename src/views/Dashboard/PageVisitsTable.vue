<template>

  <b-card body-class="p-0" header-class="border-0">
    <template v-slot:header>
      <b-row align-v="center">
        <b-col>
          <h3 class="mb-0">프로젝트 경험</h3>
        </b-col>
        <b-col class="text-right">
          <a href="#!" class="btn btn-sm btn-primary">See all</a>
        </b-col>
      </b-row>
    </template>

    <el-table class="table-responsive table project-history"
              :data="tableData"
              header-row-class-name="thead-light">
      <el-table-column label="프로젝트 명"
                       min-width="130px"
                       prop="page">
        <template v-slot="{row}">
          <div class="font-weight-600">{{row.page}}</div>
        </template>
      </el-table-column>
      <el-table-column label="프로젝트 기간"
                       min-width="100px"
                       prop="period">
      </el-table-column>
      <el-table-column label="사용 기술"
                       min-width="130px"
                       prop="skill">
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
            page: 'BuildThing IAQ Cloud',
            period: '20.09 ~ 20.10',
            skill: 'Quasar Framework, Vue.js,',
            status: '개발 완료'
          },
          {
            page: 'BuildThing IAQ Admin 앱',
            period: '20.08 ~ 20.09',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'BuildThing IAQ 앱',
            period: '20.08 ~ 20.08',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'BuildThing IAQ Cloud',
            period: '20.08 ~ 20.08',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'B.IoT v1.3',
            period: '20.03 ~ 20.10',
            skill: 'Quasar Framework, Vue.js',
            status: '유지보수 및 개발 / 완료'
          },
          {
            page: '20년 홈페이지',
            period: '20.02 ~ 20.03',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'B.IoT v1.2',
            period: '19.05 ~ 20.02',
            skill: 'Quasar Framework, Vue.js',
            status: '운영 및 유지보수 완료'
          },
          {
            page: 'A4S',
            period: '19.05 ~ 19.10',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'BuildThing Cloud',
            period: '19.05 ~ 19.05',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'MES 2.0',
            period: '18.04 ~ 18.12',
            skill: 'Quasar Framework, Vue.js',
            status: '유지보수 및 운영 중 퇴사'
          },
          {
            page: 'SWC 웹',
            period: '17.11 ~ 18.03',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'SWC 키오스크',
            period: '18.02 ~ 18.03',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: '통합 IT 시스템 구축',
            period: '19.05 ~ 19.05',
            skill: 'Quasar Framework, Vue.js',
            status: '개발 완료'
          },
          {
            page: 'SWC Wall-Pad',
            period: '17.04 ~ 17.05',
            skill: 'Quasar Framework, Vue.js',
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
</style>
