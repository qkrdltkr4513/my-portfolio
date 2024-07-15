<template>
  <div class="dashboard-wrapper">
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 dashboard-background">
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

    <!--Charts-->
    <b-container fluid class="mt--7">
      <b-row>
        <b-col xl="8" class="mb-5 mb-xl-0">
          <card type="default" header-classes="bg-transparent">
            <b-row align-v="center" slot="header">
              <b-col>
                <h5 class="h3 text-white mb-0">프로젝트 누적 수</h5>
              </b-col>
              <b-col>
                <b-nav class="nav-pills justify-content-end">
                  <b-nav-item
                    class="mr-2 mr-md-0"
                    :active="bigLineChart.activeIndex === 0"
                    link-classes="py-2 px-3"
                    @click.prevent="initBigChart(0)"
                  >
                    <span class="d-none d-md-block">전체</span>
                    <span class="d-md-none">전체</span>
                  </b-nav-item>
                </b-nav>
              </b-col>
            </b-row>
            <line-chart
              :height="350"
              ref="bigChart"
              :chart-data="bigLineChart.chartData"
              :extra-options="bigLineChart.extraOptions"
            >
            </line-chart>
          </card>
        </b-col>

        <b-col xl="4" class="mb-5 mb-xl-0">
          <card header-classes="bg-transparent">
            <b-row align-v="center" slot="header">
              <b-col>
                <h6 class="text-uppercase text-muted ls-1 mb-1"></h6>
                <h5 class="h3 mb-0">프로젝트 진행 수</h5>
              </b-col>
            </b-row>

            <bar-chart
              :height="350"
              ref="barChart"
              :chart-data="redBarChart.chartData"
            >
            </bar-chart>
          </card>
        </b-col>
      </b-row>
      <!-- End charts-->

      <!--Tables-->
      <b-row class="mt-5">
        <b-col xl="8" class="mb-5 mb-xl-0">
          <page-visits-table></page-visits-table>
        </b-col>
        <b-col xl="4" class="mb-5 mb-xl-0">
          <!-- <social-traffic-table></social-traffic-table> -->
          <card header-classes="bg-transparent">
            <b-row align-v="center" slot="header">
              <b-col>
                <!-- <h6 class="text-uppercase text-muted ls-1 mb-1"></h6> -->
                <h6 class="h3 mb-0">프로젝트 사용 기술</h6>
              </b-col>
              <b-col class="text-right">
                <a href="#/skill" class="btn btn-sm btn-primary">See all</a>
              </b-col>
            </b-row>
            <pie-chart
              :height="180"
              ref="pieChart"
              :chart-data="pieChart.chartData"
            />
          </card>
          <card header-classes="bg-transparent" style="margin-top: 30px;">
            <b-row align-v="center" slot="header">
              <b-col>
                <!-- <h6 class="text-uppercase text-muted ls-1 mb-1"></h6> -->
                <h6 class="h3 mb-0">서비스별 프로젝트</h6>
              </b-col>
              <b-col class="text-right">
                <a href="#/portfolio" class="btn btn-sm btn-primary">See all</a>
              </b-col>
            </b-row>
            <doughnut-chart
              :height="180"
              ref="doughnutChart"
              :chart-data="doughnutChart.chartData"
            />
          </card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
// Charts
import * as chartConfigs from "@/components/Charts/config";
import LineChart from "@/components/Charts/LineChart";
import BarChart from "@/components/Charts/BarChart";
import DoughnutChart from "@/components/Charts/DoughnutChart";
import PieChart from "@/components/Charts/PieChart";

// Components
import BaseProgress from "@/components/BaseProgress";
import StatsCard from "@/components/Cards/StatsCard";

// Tables
import SocialTrafficTable from "./Dashboard/SocialTrafficTable";
import PageVisitsTable from "./Dashboard/PageVisitsTable";

export default {
  components: {
    LineChart,
    BarChart,
    BaseProgress,
    StatsCard,
    PageVisitsTable,
    SocialTrafficTable,
    DoughnutChart,
    PieChart
  },
  data() {
    return {
      bigLineChart: {
        // allData: [[1, 3, 4, 5, 6, 8, 10, 15, 19, 19, 20, 21, 22, 23, 24, 25]],
        allData: [[3, 5, 8, 15, 19, 21, 23, 25]],
        label: "프로젝트 누적 수",
        activeIndex: 0,
        chartData: {
          datasets: [
            {
              label: "프로젝트 누적 수"
            }
          ]
          // labels: ['17 1/2', '17 2/2', '18 1/2', '18 2/2', '19 1/2', '19 2/2', '20 1/2', '20 2/2', '21 2/1']
        },
        extraOptions: chartConfigs.blueChartOptions
      },
      redBarChart: {
        chartData: {
          // labels: [
          //   "17 1/2",
          //   "17 2/2",
          //   "18 1/2",
          //   "18 2/2",
          //   "19 1/2",
          //   "19 2/2",
          //   "20 1/2",
          //   "20 2/2",
          //   "21 1/2",
          //   "21 2/2",
          //   "22 1/2",
          //   "22 2/2",
          //   "23 1/2",
          //   "23 2/2",
          //   "24 1/2",
          //   "24 2/2"
          // ],
          labels: [
            "2017",
            "2018",
            "2019",
            "2020",
            "2021",
            "2022",
            "2023",
            "2024"
          ],
          // datasets: [1, 2, 3, 4, 5, 6]
          datasets: [
            {
              label: "프로젝트 진행 수",
              // data: [1, 2, 1, 1, 1, 2, 2, 5, 4, 0, 1, 1, 2, 0, 1, 1]
              data: [3, 2, 3, 7, 4, 2, 2, 2]
            }
          ]
        },
        extraOptions: chartConfigs.blueChartOptions
      },
      doughnutChart: {
        chartData: {
          datasets: [
            {
              data: [18, 5, 2],
              backgroundColor: [
                "rgb(255, 99, 132)",
                "rgb(54, 162, 235)",
                "rgb(255, 205, 86)"
              ]

              // borderWidth: 10,
              // weight: 10
            }
          ],
          labels: ["Web 서비스", "App 서비스", "MES, ERP"]
          // cutoutPercentage: 50
        }
      },
      pieChart: {
        chartData: {
          datasets: [
            {
              data: [3, 8, 11, 1, 6],
              backgroundColor: [
                "rgb(31, 31, 31)",
                "#61dafb",
                "rgb(66, 184, 131)",
                "rgb(8, 126, 164)",
                "#3178c6"
              ]
            }
          ],
          labels: [
            "Next.js",
            "React.js",
            "Vue.js (앱 포함)",
            "React-Native",
            "Typescript"
          ]
        }
      }
    };
  },
  methods: {
    initBigChart(index) {
      let chartData = {
        datasets: [
          {
            label: this.bigLineChart.label,
            data: this.bigLineChart.allData[index]
          }
        ],
        // labels: [
        //   "17 1/2",
        //   "17 2/2",
        //   "18 1/2",
        //   "18 2/2",
        //   "19 1/2",
        //   "19 2/2",
        //   "20 1/2",
        //   "20 2/2",
        //   "21 1/2",
        //   "21 2/2",
        //   "22 1/2",
        //   "22 2/2",
        //   "23 1/2",
        //   "23 2/2",
        //   "24 1/2",
        //   "24 2/2"
        // ]
        labels: ["2017", "2018", "2019", "2020", "2021", "2022", "2023", "2024"]
      };
      this.bigLineChart.chartData = chartData;
      this.bigLineChart.activeIndex = index;
    }
  },
  mounted() {
    this.initBigChart(0);
  }
};
</script>
<style>
.dashboard-wrapper .dashboard-background {
  background: linear-gradient(87deg, #5eb3e482 0, #2d50ce 100%) !important;
}
.dashboard-wrapper .card .font-weight-bold {
  font-size: 16px;
}
.dashboard-wrapper .card .block {
  display: block;
}
.dashboard-wrapper .card.military-period .font-weight-bold {
  font-size: 13px;
}
.dashboard-wrapper .card.phone-number .font-weight-bold {
  font-size: 13px;
}
.main-content .header {
  padding-top: 6rem !important;
}
.el-table .cell {
  padding-left: 0px;
  padding-right: 0px;
}
</style>
