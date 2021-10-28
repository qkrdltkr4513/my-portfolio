<template>
  <card>
    <b-row align-v="center" slot="header" >
      <b-col cols="8">
        <h3 class="mb-0">본인소개 </h3>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <div class="profile-intro justify-content-center">
          <div class="mb-4">
            <i class="ic-icons ni ni-laptop"></i><p class="title heading">경력사항 (4년 5개월)</p>
            <span class="description">(주)스테이지파이브 (2021.01 ~ 재직 중)</span>
            <span class="description">(주)빌드잇 (2019.04 ~ 2020.12)</span>
            <span class="description">(주)아토스 (2017.01 ~ 2018.12)</span>
          </div>
          <hr class="my-4">
          <div class="mb-4">
            <i class="ic-icons ni ni-hat-3"></i><p class="title heading">학력사항</p>
            <span class="description">상명대학교 컴퓨터소프트웨어공학과 졸업 (2011.03 ~ 2017.02)</span>
            <span class="description">아산고등학교 졸업 (2008.03 ~ 2011.02)</span>
          </div>
          <hr class="my-4">
          <div class="mb-4">
            <i class="ic-icons ni ni-user-run"></i><span class="intro-title title heading">교내활동 및 대외활동</span>
            <!-- <span class="description">29</span> -->
            <el-table class="table-responsive table project-history"
                      :data="activationData"
                      header-row-class-name="thead-light">
              <el-table-column label="활동명"
                               min-width="90px"
                               prop="name">
                <template v-slot="{row}">
                  <div class="font-weight-600">{{row.name}}</div>
                </template>
              </el-table-column>
              <el-table-column label="기간"
                               min-width="110px"
                               prop="period">
              </el-table-column>
              <el-table-column label="기관"
                               min-width="100px"
                               prop="institute">
              </el-table-column>
              <el-table-column label="내용"
                               min-width="200px"
                               prop="content">
              </el-table-column>
            </el-table>
          </div>

          <hr class="my-4">
          <div class="mb-4">
            <i class="ic-icons ni ni-atom"></i><span class="intro-title title heading">교육 및 스터디</span>
            <el-table class="table-responsive table project-history"
                      :data="educationAndStudy"
                      header-row-class-name="thead-light">
              <el-table-column label="교육명"
                               min-width="90px"
                               prop="name">
                <template v-slot="{row}">
                  <div class="font-weight-600">{{row.name}}</div>
                </template>
              </el-table-column>
              <el-table-column label="기간"
                               min-width="90px"
                               prop="period">
              </el-table-column>
              <el-table-column label="구분"
                               min-width="110px"
                               prop="type">
              </el-table-column>
              <el-table-column label="기관"
                               min-width="100px"
                               prop="institute">
              </el-table-column>
              <el-table-column label="내용"
                               min-width="200px"
                               prop="content">
              </el-table-column>
            </el-table>
          </div>
          <div class="mb-4">
            <i class="ic-icons ni ni-badge"></i><p class="title heading">자격사항</p>
            <span class="description">지게차운전 (한국기술자격검정원 / 2014.09)</span>
            <span class="description">운전면허 1종 보통 (충남지방경찰청 / 2011.02)</span>
          </div>
        </div>
      </b-col>
    </b-row>
  </card>
</template>
<script>
import { Dropdown, DropdownItem, DropdownMenu, Table, TableColumn } from 'element-ui';
import SocialTrafficTable from '../../Dashboard/SocialTrafficTable';
import PageVisitsTable from '../../Dashboard/PageVisitsTable';
export default {
  components: {
    PageVisitsTable: PageVisitsTable,
    [Dropdown.name]: Dropdown,
    [DropdownItem.name]: DropdownItem,
    [DropdownMenu.name]: DropdownMenu,
    [Table.name]: Table,
    [TableColumn.name]: TableColumn
  },
  data() {
    return {
      user: {
        company: 'Creative Code Inc.',
        username: 'michael23',
        email: '',
        firstName: 'Mike',
        lastName: 'Andrew',
        address: 'Bld Mihail Kogalniceanu, nr. 8 Bl 1, Sc 1, Ap 09',
        city: 'New York',
        country: 'USA',
        postalCode: '',
        aboutMe: `Lamborghini Mercy, Your chick she so thirsty, I'm in that two seat Lambo.`
      },
      activationData: [
        {
          name: 'SIS',
          period: '11.03 ~ 진행중',
          institute: '상명대학교',
          content: 'S.I.S(축구) 학과 동아리 활동, 주 2회 오후 5시 ~ 7시에 타과와 친선 경기를 진행. 현재는 OB(졸업생) 동아리에 가입하여 월 1회 정기적으로 축구를 하며 연 1회 신입생과 재학생 그리고 졸업생들과 함께 MT를 진행하여 선/후배 간의 친목도모와 재학생 동아리 회장에게 축구용품, 구급품 그리고 회식비 지원 및 후배 분들이 궁금해하는 전공 분야에 대하여 적극적으로 답변을 해줌'
        },
        {
          name: '학생회장',
          period: '15.03 ~ 16.02',
          institute: '상명대학교',
          content: '학생회를 이끌며 신입생과 재학생들간의 친목 도모와 신입생들에게 학교 적응에 도움을 주며 신입생 및 재학생 그리고 규수님들 간의 월활한 소통을 할 수 있도록 중간 역할로 개선하였으며, 강의실 청소와 행사를 주로 준비와 학교 행사가 성공적으로 마무리 될 수 있도록 적극적으로 참여하며 도움'
        },
        {
          name: '인턴',
          period: '15.06 ~ 15.08',
          institute: '(주)ioot',
          content: '대학교 3학년 여름 방학 기간 동안 미세먼지 측정기 제품의 Front-End부분 참여 및 공부'
        },
        {
          name: '하이런',
          period: '15.03 ~ 16.02',
          institute: '상명대학교',
          content: '2014년 공과대 당구 동아리 회장이었던 저는 차기 회장에게 동아리 회장 직위를 인계하고, 학교 중앙 동아리에 등록 할 수 있도록 도움을 주었으며, 동아리 회원으로 타과생들과 함께 즐기며 입문자나 초보자에게 천천히 자세히 알려주며 친목도모'
        }
      ],
      educationAndStudy: [
        {
          name: '미니 프로젝트를 통한 React.js',
          period: '19.02 ~ 19.03',
          type: '스터디 모임',
          institute: '러닛',
          content: '7주간 매주 미니 프로젝트를 통해 React.js에 대한 기초와 문법 그리고 Redux와 같은 상태 관리 등에 대해 리더의 주도 하에 스터기 그룹 모임을 통해 진행'
        },
        {
          name: 'Nexacro Platform 개발자 교육',
          period: '17.11 ~ 17.11',
          type: '교육',
          institute: '투비소프트',
          content: '3일 간 Nexacro Platform를 사용하여 예제를 통한 기초 사용법 및 컴포넌트 사용법을 익힘 '
        },
        {
          name: 'Java Enterprise 고급 인력 양성',
          period: '16.06 ~ 16.12',
          type: '교육',
          institute: '비트교육센터',
          content: 'Java, JSP, JavaScript 언어를 통해 Spring Framework 사용법을 배우고 배운 것을 바탕으로 음원믹싱 서비스를 제공하는 프로젝트를 진행'
        },
      ]
    };
  },
  methods: {
    updateProfile() {
      alert('Your data: ' + JSON.stringify(this.user));
    }
  }
};
</script>
<style>
.profile-intro .intro-title {
  display: block;
  margin-bottom: 1rem;
}
.profile-intro .ic-icons{
  display: inline-block;
  vertical-align: middle;
  margin-bottom: 3px;
  margin-right: 6px;
}
.profile-intro .title {
  display: inline-block;
}
.profile-intro .description {
  display: block;
}
.profile-intro .el-table::before {
  height: 0;
}
</style>
