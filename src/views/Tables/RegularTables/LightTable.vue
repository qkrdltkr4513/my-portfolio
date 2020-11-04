<template>
    <b-card no-body class="portfolio-summary-wrapper">
        <b-card-header class="border-0">
            <h3 class="mb-0">프로젝트 경험 요약</h3>
        </b-card-header>

        <el-table class="table-responsive table project-summary"
                  header-row-class-name="thead-light"
                  :data="projects">
            <el-table-column label="프로젝트 명"
                             min-width="160px"
                             prop="name"
                             class="summary-table">
                <template v-slot="{row}">
                    <b-media no-body class="align-items-center">
                      <span class="font-weight-600 name mb-0 text-sm">{{row.title}}</span>
                    </b-media>
                </template>
            </el-table-column>

            <el-table-column label="기간"
                             prop="period"
                             min-width="100px">
            </el-table-column>

            <el-table-column label="담당 업무"
                             prop="type"
                             min-width="140px">
            </el-table-column>

            <el-table-column label="사용 기술"
                             prop="useSkill"
                             min-width="310px">
            </el-table-column>

            <el-table-column label="진행 상태"
                             min-width="80px"
                             prop="status">
                <template v-slot="{row}">
                    <badge class="badge-dot mr-4" type="">
                        <i :class="`bg-${row.statusType}`"></i>
                        <span class="status" :class="`text-${row.statusType}`">{{row.status}}</span>
                    </badge>
                </template>
            </el-table-column>

        </el-table>

        <!-- <b-card-footer class="py-4 d-flex justify-content-end">
            <base-pagination v-model="currentPage" :per-page="10" :total="50"></base-pagination>
        </b-card-footer> -->
    </b-card>
</template>
<script>
  import projects from './../projects'
  import { Table, TableColumn} from 'element-ui'
  export default {
    name: 'light-table',
    components: {
      [Table.name]: Table,
      [TableColumn.name]: TableColumn
    },
    data() {
      return {
        projects,
        currentPage: 1
      };
    }
  }
</script>
<style>
.portfolio-summary-wrapper .project-summary .el-table__body-wrapper {
  max-height: 500px;
  overflow-y: auto;
}

</style>
