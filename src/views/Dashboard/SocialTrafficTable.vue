<template>
  <b-card body-class="p-0" header-class="border-0">
    <template v-slot:header>
      <b-row align-v="center">
        <b-col class="col-skill">
          <h3 class="mb-0 mr-2 skill-stack-text" @mouseover="mouseOver" @mouseleave="mouseLeave">기술 스택</h3>
          <span class="ni ni-active-40 skill-stack-info" @mouseover="mouseOver" @mouseleave="mouseLeave"></span>
          <div v-show="showInfoMessage" class="info-message">
            <h6>0% 이상 - 하</h6>
            <h6>35% 이상 - 중</h6>
            <h6>75% 이상 - 상</h6>
          </div>
          <!-- <h6 class="mb-0"></h6> -->
        </b-col>
        <b-col class="text-right">
          <base-button size="sm" type="primary">See all</base-button>
        </b-col>
      </b-row>
    </template>


    <el-table
      class="table-responsive table skill-stack"
      :data="tableData"
      header-row-class-name="thead-light">
      <el-table-column label="이름" min-width="130px" prop="name">
        <template v-slot="{row}">
          <div class="font-weight-600">{{row.name}}</div>
        </template>
      </el-table-column>

      <el-table-column label="수준" min-width="110px" prop="level">
      </el-table-column>

      <el-table-column label="숙련도" min-width="220px" prop="figure">
        <template v-slot="{row}">
          <div class="d-flex align-items-center">
            <span class="mr-2">{{row.figure}}%</span>
            <base-progress :type="row.progressType" :value="row.figure" />
          </div>
        </template>
      </el-table-column>
    </el-table>
  </b-card>
</template>
<script>
  import { BaseProgress } from '@/components';
  import { Table, TableColumn, DropdownMenu, DropdownItem, Dropdown} from 'element-ui'
  export default {
    name: 'social-traffic-table',
    components: {
      BaseProgress,
      [Table.name]: Table,
      [TableColumn.name]: TableColumn,
      [Dropdown.name]: Dropdown,
      [DropdownItem.name]: DropdownItem,
      [DropdownMenu.name]: DropdownMenu,
    },
    data() {
      return {
        showInfoMessage: false,
        tableData: [
          {
            name: 'Quasar Framework',
            level: '중',
            figure: 60,
            progressType: 'gradient-success',
          },
          {
            name: 'Spring Framework',
            level: '중',
            figure: 40,
            progressType: 'gradient-primary',
          },
          {
            name: 'Vue.js',
            level: '중',
            figure: 65,
            progressType: 'gradient-info',
          },
          {
            name: 'jQuery',
            level: '중',
            figure: 65,
            progressType: 'gradient-info',
          },
          {
            name: 'TypeScript',
            level: '하',
            figure: 30,
            progressType: 'gradient-warning',
          },
          {
            name: 'JavaScript',
            level: '중',
            figure: 65,
            progressType: 'gradient-info',
          },
          {
            name: 'HTML5',
            level: '중',
            figure: 60,
            progressType: 'gradient-success',
          },
          {
            name: 'CSS3',
            level: '중',
            figure: 60,
            progressType: 'gradient-success',
          },
          {
            name: 'Stylus',
            level: '중',
            figure: 60,
            progressType: 'gradient-success',
          },
          {
            name: 'Kendo UI',
            level: '중',
            figure: 65,
            progressType: 'gradient-info',
          },
          {
            name: 'Java',
            level: '하',
            figure: 30,
            progressType: 'gradient-warning',
          },
          {
            name: 'Oracle',
            level: '하',
            figure: 30,
            progressType: 'gradient-warning',
          }
        ]
      }
    },
    methods: {
      mouseOver () {
        const that = this
        that.showInfoMessage = true
      },
      mouseLeave () {
        const that = this
        that.showInfoMessage = false
      }
    }

  }
</script>
<style>
.skill-stack {
  max-height: 500px;
  overflow: auto;
}
.skill-stack-text {
  display: inline-block;
}
.skill-stack-info {
  font-size: 14px;
}

.skill-stack-text, .skill-stack-info
  :hover {
    cursor: pointer;
  }
.skill-stack-info, .skill-stack-text
  :hover {
    cursor: pointer;
  }

.info-message {
  position: absolute;
  z-index: 2;
  width: 90px;
  height: 70px;
  top: 3px;
  left: 130px;
  padding: 5px 10px;
  background-color: #F6F9FC;
  border: 1px solid #707070;
  border-radius: 7px;
}
</style>
