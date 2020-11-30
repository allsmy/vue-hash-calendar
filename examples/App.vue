/**
* @Description:    vue-hash-calendar-slide 移动端日期、时间选择插件，日期选择面板以日历形式展示。支持上下滑动切换日期、时间
* @Author:         TSY
* @CreateDate:     2019/05/23 00:08
* @Email:          t@tsy6.com
*/
<template>
  <div class="body">
    <vue-hash-calendar-slide ref="picker"
                       model="dialog"
                       :scroll-change-date="true"
                       :visible.sync="isShowCalendar"
                       :default-datetime="defaultDatetime"
                       :is-show-week-view="false"
                       :minute-step="1"
                       :mark-date="markDate"
                       :disabled-date="disabledDate"
                       week-start="sunday"
                       picker-type="datetime"
                       :show-today-button="true"
                       :disabled-week-view="false"
                       :mainBackgroundColor="'rgb(140 110 110)'"
                       :disableColor="'#c0c4cc'"
                       :contentColor="'rgb(239,190,6)'"
                       :circleBackgroundColor="'rgb(26,2,2)'"
                       :calendarWeekColor="'rgb(26,26,24)'"
                       :maskLinearGradient="'linear-gradient(rgba(255,255,255,0.5), rgba(255, 255, 255, 1))'"
                       format="YY/MM/DD hh:mm"
                       lang="CN"
                       @confirm="dateConfirm"
                       @click="dateClick"
                       @change="dateChange"
                       @height="heightChange">
    </vue-hash-calendar-slide>
  </div>
</template>

<script>

export default {
  name: 'demo',
  data() {
    return {
      isShowCalendar: true, // 是否显示弹窗
      isShowTips: false, // 是否显示下载提示
      defaultDatetime: new Date(),
      markDate: [
        { color: 'rgba(255,255,255,0.3)', type: 'background', date: ['2020/02/25', '2020/03/25', '2020/04/25', '2020/05/25', '2020/06/25', '2020/07/25', '2020/08/25', '2020/09/25', '2020/10/25', '2020/11/25', '2020/12/25'] },
        { color: '#c62626', type: 'dot', date: ['2020/01/20', '2020/02/20', '2020/03/20', '2020/04/20', '2020/05/20', '2020/06/20', '2020/07/20', '2020/08/20', '2020/09/20', '2020/10/20', '2020/11/20', '2020/12/20'] },
        { color: '#133fcf', type: 'dot', date: ['2020/01/12', '2020/02/12', '2020/03/12', '2020/04/12', '2020/05/12', '2020/06/12', '2020/07/12', '2020/08/12', '2020/09/12', '2020/10/12', '2020/11/12', '2020/12/12'] },
        { color: '#000000', type: 'dot', date: ['2020/01/29', '2020/02/29', '2020/03/29', '2020/04/29', '2020/05/29', '2020/06/29', '2020/07/29', '2020/08/29', '2020/09/29', '2020/10/29', '2020/11/29', '2020/12/29'] }
      ], // 对象数组形式的标记日期，可以自定义标记颜色
      calendarHeight: 0
    }
  },
  watch: {
    calendarHeight: function(n, o) {

    }
  },
  methods: {
    showCalendarDialog() { // 显示日历
      this.isShowCalendar = true
    },
    dateChange(date) { // 日期改变触发
      console.log(date, 'change')
    },
    dateConfirm(date) { // 点击确认按钮触发
      console.log(date, 'confirm')
    },
    dateClick(date) { // 点击日期时按钮触发
      console.log(date, 'click')
    },
    disabledDate(date) { // 禁用的日期
      return false
      // let timestamp = date.getTime()
      // let oneDay = 24 * 60 * 60 * 1000
      //
      // if (timestamp < new Date().getTime() - oneDay) {
      //   return true
      // }
      //
      // return false
    },
    heightChange(height) {
      this.calendarHeight = height
      this.$emit('height', height)
    }
  }
}
</script>
