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
                       :maskLinearGradientButtonIcon="'data:image/png;base64,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'"
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
