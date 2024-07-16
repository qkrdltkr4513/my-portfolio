<template>
  <b-card body-class="p-0" header-class="border-0">
    <template v-slot:header>
      <b-row align-v="center">
        <b-col class="col-skill">
          <h3
            class="mb-0 mr-2 skill-stack-text"
            @mouseover="mouseOver"
            @mouseleave="mouseLeave"
          >
            보유 기술
          </h3>
          <div style="margin-top: 20px;">
            <p class="mt-3 mb-0 text-sm">
              <span
                style="display: inline-block; border: 1px solid ; border-radius: 12px; padding: 6px; margin: 0 6px 6px 0; "
                v-for="item in skillList"
                >{{ item }}</span
              >
            </p>
          </div>
          <!-- <span
            class="ni ni-active-40 skill-stack-info"
            @mouseover="mouseOver"
            @mouseleave="mouseLeave"
          ></span>
          <div v-show="showInfoMessage" class="info-message">
            <h6>75% 이상 - 상</h6>
            <h6>35% 이상 - 중</h6>
            <h6>0% 이상 - 하</h6>
          </div> -->
          <!-- <h6 class="mb-0"></h6> -->
        </b-col>
        <!-- <b-col class="text-right">
          <a href="#/skill" class="btn btn-sm btn-primary">See all</a>
        </b-col> -->
      </b-row>
    </template>

    <!-- <el-table
      class="table-responsive table skill-stack"
      :data="tableData"
      header-row-class-name="thead-light"
    > -->
    <!-- <el-table__body></el-table__body> -->
    <!-- <el-table-column label="이름" min-width="130px" prop="name">
        <template v-slot="{ row }">
          <div class="font-weight-600 project-history-skill">
            {{ row.name }}
          </div>
        </template>
      </el-table-column> -->

    <!-- <el-table-column label="수준" min-width="80px" prop="level">
      </el-table-column> -->

    <!-- <el-table-column label="숙련도" min-width="250px" prop="figure">
        <template v-slot="{ row }">
          <div class="d-flex align-items-center">
            <span class="mr-2">{{ row.figure }}%</span>
            <base-progress
              class="progress-bar"
              :type="row.progressType"
              :value="row.figure"
            />
            <span
              v-show="
                row.name === 'Java' ||
                row.name === 'Oracle' ||
                row.name === 'Spring Framework'
                  ? false
                  : true
              "
              :class="[
                row.name !== 'Java' &&
                row.name !== 'Oracle' &&
                row.name !== 'Spring Framework'
                  ? 'ic-arrow text-success'
                  : 'text-danger'
              ]"
            >
              <i class="fa fa-arrow-up"></i>
            </span>
            <span
              v-show="
                row.name === 'Java' ||
                row.name === 'Oracle' ||
                row.name === 'Spring Framework'
                  ? true
                  : false
              "
              :class="[
                row.name === 'Java' ||
                row.name === 'Oracle' ||
                row.name === 'Spring Framework'
                  ? 'ic-arrow text-danger'
                  : 'text-success'
              ]"
            >
              <i class="fa fa-arrow-down"></i>
            </span>
          </div>
        </template>
      </el-table-column> -->
    <!-- </el-table> -->
  </b-card>
</template>
<script>
import { BaseProgress } from "@/components";
import {
  Table,
  TableColumn,
  DropdownMenu,
  DropdownItem,
  Dropdown
} from "element-ui";
export default {
  name: "social-traffic-table",
  components: {
    BaseProgress,
    [Table.name]: Table,
    [TableColumn.name]: TableColumn,
    [Dropdown.name]: Dropdown,
    [DropdownItem.name]: DropdownItem,
    [DropdownMenu.name]: DropdownMenu
  },
  data() {
    return {
      showInfoMessage: false,
      tableData: [
        {
          name: "Quasar Framework",
          level: "중",
          figure: 60,
          progressType: "gradient-success"
        },
        {
          name: "Vue.js",
          level: "중",
          figure: 70,
          progressType: "gradient-info"
        },
        {
          name: "React.js",
          level: "중",
          figure: 55,
          progressType: "gradient-success"
        },
        {
          name: "Next.js",
          level: "하",
          figure: 20,
          progressType: "gradient-warning"
        },
        {
          name: "GatsBy",
          level: "하",
          figure: 30,
          progressType: "gradient-warning"
        },
        {
          name: "jQuery",
          level: "중",
          figure: 65,
          progressType: "gradient-info"
        },
        {
          name: "TypeScript",
          level: "중",
          figure: 40,
          progressType: "gradient-success"
        },
        {
          name: "JavaScript",
          level: "중",
          figure: 65,
          progressType: "gradient-info"
        },
        {
          name: "HTML5",
          level: "중",
          figure: 60,
          progressType: "gradient-success"
        },
        {
          name: "CSS3",
          level: "중",
          figure: 60,
          progressType: "gradient-success"
        },
        {
          name: "Stylus",
          level: "중",
          figure: 60,
          progressType: "gradient-success"
        },
        {
          name: "Styled-component",
          level: "중",
          figure: 40,
          progressType: "gradient-success"
        },
        {
          name: "Emotion",
          level: "중",
          figure: 40,
          progressType: "gradient-success"
        },
        {
          name: "Kendo UI",
          level: "중",
          figure: 65,
          progressType: "gradient-info"
        }
      ],
      skillList: [
        "Next.js",
        "React.js",
        "Quasar Framework",
        "Vue.js",
        "React-Native",
        "Typescript",
        "Javascript",
        "HTML5",
        "CSS3",
        "Stylus",
        "Styled-component",
        "Emotion",
        "Redux",
        "Recoil",
        "React-Query",
        "jQuery",
        "Kendo UI"
      ]
    };
  },
  methods: {
    mouseOver() {
      const that = this;
      that.showInfoMessage = true;
    },
    mouseLeave() {
      const that = this;
      that.showInfoMessage = false;
    }
  }
};
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

.skill-stack-text,
.skill-stack-info :hover {
  cursor: pointer;
}
.skill-stack-info,
.skill-stack-text :hover {
  cursor: pointer;
}

.skill-stack .ic-arrow {
  margin-left: 15px;
}

.info-message {
  position: absolute;
  z-index: 2;
  width: 90px;
  height: 70px;
  top: 3px;
  left: 130px;
  padding: 5px 10px;
  background-color: #f6f9fc;
  border: 1px solid #707070;
  border-radius: 7px;
}

.el-table::before {
  height: 0px;
}

@media screen and (max-width: 500px) {
  /* .table.skill-stack .el-table__body {
    width: auto !important;
  } */
  /* .table.skill-stack .el-table__header th{
    padding-right: 0
  } */
  .project-history-skill {
    display: -webkit-box;
    max-width: 130px;
    white-space: pre-wrap;
    text-overflow: ellipsis;
    overflow: hidden;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }
}
</style>
