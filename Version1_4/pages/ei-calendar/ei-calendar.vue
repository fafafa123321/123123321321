<template>
	<view class="page">
    date:
    <view v-for="(item, index) in date" :key="index">{{item}}</view>
    <button @click="show = true">GGH欢迎你,欢迎来到我这里!</button>
		<ei-calendar ref="calendar" :drawer="false" :disabled="false" title="DATA" @date-change="change" :visible.sync="show" type="range" :disabledDate="disabledDate" v-model="date" :custom-date="customDate" format="YYYY-MM-DD">
    </ei-calendar>
	</view>
</template>

<script>
	import EiCalendar from '@/components/ei-calendar/ei-calendar';

	export default {
    components: {EiCalendar},
    data() {
			return {
			  show: true,
         date: [new Date('2023-11-17')],
        customDate: [
          {
            cellClass: 'custom-cell',
            date: '2023-11-17',
            top: [
              {
                class: 'custom-cell-top-1',
                text: ' '
              },
              {
                class: 'custom-cell-top-2',
                text: '√'
              }
            ]
          }]
			}
		},
		methods: {
     changeCustomData() {
       const today = new Date(); // 获取今天的日期
       const year = today.getFullYear();
       const month = String(today.getMonth() + 1).padStart(2, '0'); // 月份需要补零
       const day = String(today.getDate()).padStart(2, '0'); // 天数需要补零
     
       this.customDate = [{
         cellClass: 'custom-cell',
         date: `${year}-${month}-${day}`, // 设置为今天的日期
         top: [
           {
             class: 'custom-cell-top-1',
             text: '今天'
           },
           {
             class: 'custom-cell-top-2',
             text: '√'
           }
         ]
       }];
       this.$refs.calendar.refresh(); // 刷新日历选择器组件
     },
      change(a, b) {
        debugger;
      }
		}
	}
</script>

<style lang="scss">
  .page {
    background: #f8f8f8;
    height: 100vh;
    font-size: 28upx;
  }
  .custom-cell {
    color: #4cd964;
  }
  .custom-cell-top-1 {
    color: #ccc;
  }
  .custom-cell-top-2 {
    color: red;
  }
</style>
