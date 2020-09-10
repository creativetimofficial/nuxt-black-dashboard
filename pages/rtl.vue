<template>
  <div>
    <div class="row">
      <div class="col-12">
        <card type="chart">
          <template slot="header">
            <div class="row">
              <div class="col-sm-6" :class="isRTL ? 'text-right' : 'text-left'">
                <h5 class="card-category">مجموع الشحنات</h5>
                <h2 class="card-title">أداء</h2>
              </div>
              <div class="col-sm-6 d-flex d-sm-block">
                <div
                  class="btn-group btn-group-toggle"
                  :class="isRTL ? 'float-left' : 'float-right'"
                  data-toggle="buttons"
                >
                  <label
                    v-for="(option, index) in bigLineChartCategories"
                    :key="option.name"
                    class="btn btn-sm btn-primary btn-simple"
                    :class="{ active: bigLineChart.activeIndex === index }"
                    :id="index"
                  >
                    <input
                      type="radio"
                      @click="initBigChart(index)"
                      name="options"
                      autocomplete="off"
                      :checked="bigLineChart.activeIndex === index"
                    />
                    <span class="d-none d-sm-block">{{ option.name }}</span>
                    <span class="d-block d-sm-none">
                      <i :class="option.icon"></i>
                    </span>
                  </label>
                </div>
              </div>
            </div>
          </template>
          <div class="chart-area">
            <line-chart
              style="height: 100%"
              ref="bigChart"
              :chart-data="bigLineChart.chartData"
              :gradient-colors="bigLineChart.gradientColors"
              :gradient-stops="bigLineChart.gradientStops"
              :extra-options="bigLineChart.extraOptions"
            >
            </line-chart>
          </div>
        </card>
      </div>

      <div class="col-lg-4" :class="{ 'text-right': isRTL }">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">مجموع الشحنات</h5>
            <h3 class="card-title">
              <i class="tim-icons icon-bell-55 text-primary "></i> 763,215
            </h3>
          </template>
          <div class="chart-area">
            <line-chart
              style="height: 100%"
              :chart-data="purpleLineChart.chartData"
              :gradient-colors="purpleLineChart.gradientColors"
              :gradient-stops="purpleLineChart.gradientStops"
              :extra-options="purpleLineChart.extraOptions"
            >
            </line-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-4" :class="{ 'text-right': isRTL }">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">المبيعات اليومية</h5>
            <h3 class="card-title">
              <i class="tim-icons icon-delivery-fast text-info "></i> 3,500€
            </h3>
          </template>
          <div class="chart-area">
            <bar-chart
              style="height: 100%"
              :chart-data="blueBarChart.chartData"
              :gradient-stops="blueBarChart.gradientStops"
              :extra-options="blueBarChart.extraOptions"
            >
            </bar-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-4" :class="{ 'text-right': isRTL }">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">المهام المكتملة</h5>
            <h3 class="card-title">
              <i class="tim-icons icon-send text-success "></i> 12,100K
            </h3>
          </template>
          <div class="chart-area">
            <line-chart
              style="height: 100%"
              :chart-data="greenLineChart.chartData"
              :gradient-stops="greenLineChart.gradientStops"
              :extra-options="greenLineChart.extraOptions"
            >
            </line-chart>
          </div>
        </card>
      </div>

      <div class="col-lg-6">
        <card type="tasks" :header-classes="{ 'text-right': isRTL }">
          <template slot="header">
            <h6 class="title d-inline">مهام 5</h6>
            <p class="card-category d-inline">اليوم</p>
            <base-dropdown
              menu-on-right=""
              tag="div"
              title-classes="btn btn-link btn-icon"
              :class="{ 'float-left': isRTL }"
            >
              <i slot="title" class="tim-icons icon-settings-gear-63"></i>
              <a class="dropdown-item" href="#pablo"> عمل </a>
              <a class="dropdown-item" href="#pablo"> عمل آخر </a>
              <a class="dropdown-item" href="#pablo"> شيء آخر </a>
            </base-dropdown>
          </template>
          <div class="table-full-width table-responsive">
            <base-table :data="tableDataTask" thead-classes="text-primary">
              <template slot-scope="{ row }">
                <td><base-checkbox v-model="row.done"></base-checkbox></td>
                <td>
                  <p class="title">{{ row.title }}</p>
                  <p class="text-muted">{{ row.description }}</p>
                </td>
                <td class="td-actions text-right">
                  <el-tooltip
                    content="Edit task"
                    effect="light"
                    :open-delay="300"
                    placement="top"
                  >
                    <base-button type="link">
                      <i class="tim-icons icon-pencil"></i>
                    </base-button>
                  </el-tooltip>
                </td>
              </template>
            </base-table>
          </div>
        </card>
      </div>
      <div class="col-lg-6">
        <card card-body-classes="table-full-width">
          <h4 slot="header" class="card-title" :class="{ 'text-right': isRTL }">جدول بسيط</h4>
          <el-table :data="tableData">
            <el-table-column
              min-width="150"
              sortable
              align="left"
              header-align="left text-left"
              label="اسم"
              property="name"
            ></el-table-column>
            <el-table-column
              min-width="150"
              sortable
              align="left"
              header-align="left text-left"
              label="بلد"
              property="country"
            ></el-table-column>
            <el-table-column
              min-width="150"
              sortable
              align="left"
              header-align="left text-left"
              label="مدينة"
              property="city"
            ></el-table-column>
            <el-table-column
              min-width="150"
              sortable
              align="left"
              header-align="left text-left"
              label="راتب"
              property="salary"
            ></el-table-column>
          </el-table>
        </card>
      </div>
    </div>
  </div>
</template>
<script>
import { BaseTable } from '@/components';
import LineChart from '@/components/Charts/LineChart';
import BarChart from '@/components/Charts/BarChart';
import * as chartConfigs from '@/components/Charts/config';
import config from '@/config';
import { Table, TableColumn } from 'element-ui';

let bigChartData = [
  [100, 70, 90, 70, 85, 60, 75, 60, 90, 80, 110, 100],
  [80, 120, 105, 110, 95, 105, 90, 100, 80, 95, 70, 120],
  [60, 80, 65, 130, 80, 105, 90, 130, 70, 115, 60, 130]
]
let bigChartLabels = ['JAN', 'FEB', 'MAR', 'APR', 'MAY', 'JUN', 'JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC']
let bigChartDatasetOptions = {
  fill: true,
  borderColor: config.colors.primary,
  borderWidth: 2,
  borderDash: [],
  borderDashOffset: 0.0,
  pointBackgroundColor: config.colors.primary,
  pointBorderColor: 'rgba(255,255,255,0)',
  pointHoverBackgroundColor: config.colors.primary,
  pointBorderWidth: 20,
  pointHoverRadius: 4,
  pointHoverBorderWidth: 15,
  pointRadius: 4,
}

import {
  BaseSwitch,
  TimeLine,
  TimeLineItem,
  BaseCheckbox
} from '@/components';

export default {
  name: 'rtl',
  components: {
    BaseTable,
    LineChart,
    BarChart,
    [Table.name]: Table,
    [TableColumn.name]: TableColumn
  },
  data() {
    return {
      allContributions: true,
      pastWeekContributions: false,
      bigLineChart: {
        activeIndex: 0,
        chartData: {
          datasets: [{
            ...bigChartDatasetOptions,
            data: bigChartData[0]
          }],
          labels: bigChartLabels
        },
        extraOptions: chartConfigs.purpleChartOptions,
        gradientColors: config.colors.primaryGradient,
        gradientStops: [1, 0.4, 0],
        categories: []
      },
      tableDataTask: [
        {
          title: 'مركز معالجة موقع محور',
          description: 'نص آخر هناالوثائق',
          done: false
        },
        {
          title: 'لامتثال GDPR',
          description:
            'الناتج المحلي الإجمالي هو نظام يتطلب من الشركات حماية البيانات الشخصية والخصوصية لمواطني أوروبا بالنسبة للمعاملات التي تتم داخل الدول الأعضاء في الاتحاد الأوروبي.',
          done: true
        },
        {
          title: 'القضاياالقضايا',
          description:
            'سيكونونقال 50٪ من جميع المستجيبين أنهم سيكونون أكثر عرضة للتسوق في شركة',
          done: false
        },
        {
          title: 'تصدير الملفات التي تمت معالجتها',
          description: 'كما يبين التقرير أن المستهلكين لن يغفروا شركة بسهولة بمجرد حدوث خرق يعرض بياناتهم الشخصية.',
          done: false
        },
        {
          title: 'الوصول إلى عملية التصدير',
          description:
            'سياسة السيء إنطلاق في قبل, مساعدة والمانيا أخذ قد. بل أما أمام ماشاء الشتاء،, تكاليف الإقتصادي بـ حين. ٣٠ يتعلّق للإتحاد ولم, وتم هناك مدينة بتحدّي إذ, كان بل عمل',
          done: false
        },
        {
          title: 'الافراج عن v2.0.0',
          description: 'عن رئيس طوكيو البولندي لمّ, مايو مرجع وباءت قبل هو, تسمّى الطريق الإقتصادي ذات أن. لغات الإطلاق الفرنسية دار ان, بين بتخصيص الساحة اقتصادية أم. و الآخ',
          done: false
        }
      ],
      tableData: [
        {
          id: 1,
          name: 'رايس داكوتا	',
          salary: '$36.738',
          country: 'النيجر	',
          city: 'العود-تورنهاوت	'
        },
        {
          id: 2,
          name: 'مينيرفا هوبر	',
          salary: '$23,789',
          country: 'كوراساو',
          city: 'Sinaai-واس	'
        },
        {
          id: 3,
          name: 'سيج رودريجيز	',
          salary: '$56,142',
          country: 'هولندا',
          city: 'بايلي'
        },
        {
          id: 4,
          name: 'فيليب شانيه	',
          salary: '$38,735',
          country: 'كوريا، جنوب	',
          city: 'اوفرلاند بارك	'
        },
        {
          id: 5,
          name: 'Doris Greene',
          salary: '$63,542',
          country: 'مالاوي	',
          city: 'المنع	'
        }
      ],
      purpleLineChart: {
        extraOptions: chartConfigs.purpleChartOptions,
        chartData: {
          labels: ['JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC'],
          datasets: [
            {
              label: 'Data',
              fill: true,
              borderColor: config.colors.primary,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.primary,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.primary,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [80, 100, 70, 80, 120, 80]
            }
          ]
        },
        gradientColors: config.colors.primaryGradient,
        gradientStops: [1, 0.2, 0]
      },
      greenLineChart: {
        extraOptions: chartConfigs.greenChartOptions,
        chartData: {
          labels: ['JUL', 'AUG', 'SEP', 'OCT', 'NOV'],
          datasets: [
            {
              label: 'My First dataset',
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [90, 27, 60, 12, 80]
            }
          ]
        },
        gradientColors: [
          'rgba(66,134,121,0.15)',
          'rgba(66,134,121,0.0)',
          'rgba(66,134,121,0)'
        ],
        gradientStops: [1, 0.4, 0]
      },
      blueBarChart: {
        extraOptions: chartConfigs.barChartOptions,
        chartData: {
          labels: ['USA', 'GER', 'AUS', 'UK', 'RO', 'BR'],
          datasets: [
            {
              label: 'Countries',
              fill: true,
              borderColor: config.colors.info,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              data: [53, 20, 10, 80, 100, 45]
            }
          ]
        },
        gradientColors: config.colors.primaryGradient,
        gradientStops: [1, 0.4, 0]
      }
    };
  },
  methods: {
    initBigChart (index) {
      let chartData = {
        datasets: [{
          ...bigChartDatasetOptions,
          data: bigChartData[index]
        }],
        labels: bigChartLabels
      };
      this.$refs.bigChart.updateGradients(chartData);
      this.bigLineChart.chartData = chartData;
      this.bigLineChart.activeIndex = index;
    }
  },
  mounted() {
    this.$rtl.enableRTL();
    this.initBigChart(0);
  },
  computed: {
    enableRTL () {
      return this.$route.query.enableRTL;
    },
    isRTL () {
      return this.$rtl.isRTL;
    },
    bigLineChartCategories () {
      return [{ name: ' حسابات ', icon: 'tim-icons icon-single-02' }, {
        name: ' المشتريات ',
        icon: 'tim-icons icon-gift-2'
      }, { name: ' جلسات ', icon: 'tim-icons icon-tap-02' }];
    }
  },
  beforeDestroy() {
    this.switchLocalePath('en')
    this.$rtl.disableRTL();
  }
};
</script>
<style></style>
