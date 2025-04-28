<template>
  <div class="home-wrapper">
    <div class="date-row">
      <div v-for="(item, index) in cardInfoData" :key="index" class="data-col">
        <el-card shadow="always" :body-style="{padding: '0px'}">
          <div class="date-block">
            <i :class="[ item.icon ]" :style="{ background: item.color }" class="icon-box" />
            <div class="date-cont">
              <CountTo class="count" :start-val="0" :end-val="item.count" :duration="3000" />
              <p class="title">{{ item.title }}</p>
            </div>
          </div>
        </el-card>
      </div>
    </div>
    <el-row class="date-box" :gutter="20">
      <el-col :span="8">
        <el-card shadow="always" :body-style="{padding: '0px'}">
          <ChartsPie :title="text" type="pie" :data="chartsPieData" class="data-desc" />
        </el-card>
      </el-col>
      <el-col :span="8">
        <el-card shadow="always" :body-style="{padding: '0px'}">
          <div class="data-desc data-lang-box">
            <div class="data-lang-title">宠物种类构成</div>
            <div v-for="(item, index) in langsData" :key="index" class="data-lang-item">
              <label>{{ item.name }}</label>
              <el-progress :percentage="item.value" :stroke-width="16" :color="item.color" />
            </div>
          </div>
        </el-card>
      </el-col>
      <el-col :span="8">
        <el-card shadow="always" :body-style="{padding: '0px'}">
          <ChartsPie :title="text" type="ring" :data="chartsPieData" class="data-desc" />
        </el-card>
      </el-col>
    </el-row>
    <el-row class="date-box" :gutter="20">
      <el-col :span="12">
        <el-card shadow="always" :body-style="{padding: '0px'}">
          <ChartsBar :title="title" :data="commonChartsData" class="data-chart" />
        </el-card>
      </el-col>
      <el-col :span="12">
        <el-card shadow="always" :body-style="{padding: '0px'}">
          <ChartsLine :title="title" :data="commonChartsData" class="data-chart" />
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import CountTo from 'vue-count-to'
import ChartsPie from '@/components/Charts/ChartsPie'
import ChartsBar from '@/components/Charts/ChartsBar'
import ChartsLine from '@/components/Charts/ChartsLine'
export default {
  name: 'Home',
  components: { CountTo, ChartsPie, ChartsBar, ChartsLine },
  data() {
    return {
      text: '宠物访问来源',
      title: '近七天宠物店访问量条形图',
      langsData: [
        { name: '猫咪', value: 45, color: '#2d8cf0' },
        { name: '狗狗', value: 32, color: '#19be6b' },
        { name: '鸟类', value: 4, color: '#ff9900' },
        { name: '鱼类', value: 13, color: '#e46cbb' },
        { name: '小动物', value: 6, color: '#9a66e4' }
      ],
      cardInfoData: [
        { title: '今日到访', icon: 'vue-dsn-icon-dianji', count: 682, color: '#2d8cf0' },
        { title: '新增顾客', icon: 'vue-dsn-icon-xinzeng', count: 259, color: '#19be6b' },
        { title: '商品购买', icon: 'vue-dsn-icon-xinfeng', count: 1262, color: '#ff9900' },
        { title: '点赞数量', icon: 'vue-dsn-icon-dianzan', count: 508, color: '#e46cbb' },
        { title: '累计收藏', icon: 'vue-dsn-icon-heart', count: 379, color: '#9a66e4' }
      ],
      chartsPieData: [
        { value: 1920, name: '直接到访' },
        { value: 1169, name: '邮件营销' },
        { value: 986, name: '广告推广' },
        { value: 621, name: '视频广告' },
        { value: 3256, name: '搜索引擎' }
      ],
      commonChartsData: {
        Mon: 782,
        Tue: 925,
        Wed: 1196,
        Thu: 812,
        Fri: 328,
        Sat: 222,
        Sun: 1080
      }
    }
  }
}
</script>

<style lang="less">
@import "../assets/less/home";
</style>
