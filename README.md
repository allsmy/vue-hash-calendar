![calendar.gif](https://www.allsmy.com/resource/vue-hash-calendar-slide.gif)

# vue-hash-calendar-slide

- 增加禁用日期颜色控制
- 增加外部传参控制上下滑动，方便复杂页面集成
- 修复左右滑动过程中触发点击事件的bug
- 增加更换背景色
- 增加日期背景色标记
- 基于 vue 2.X 开发的日历组件
- 支持手势滑动操作
- 原生 js 开发，没引入第三方库
- 上下滑动 切换 周/月 模式
- 更多更新查看提交日志：
https://github.com/allsmy/vue-hash-calendar-slide/commits/master

# 安装使用说明

```
npm i vue-hash-calendar-slide
```

```
// 在入口文件中（main.js），导入组件库
import vueHashCalendarSlide from 'vue-hash-calendar-slide'
// 引入组件CSS样式
import 'vue-hash-calendar-slide/lib/vue-hash-calendar-slide.css'
// 注册组件库
Vue.use(vueHashCalendarSlide)
```

```
// 在VUE文件中引入组件
 <vue-hash-calendar-slide></vue-hash-calendar-slide>
```

## github 地址：[https://github.com/allsmy/vue-hash-calendar-slide](https://github.com/allsmy/vue-hash-calendar-slide)

# API

| 属性             | 说明                                                                                                                                                  |   类型   |      默认      | 是否必传 |
| :--------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------- | :------: | :------------: | :------: |
| disableColor     | 非当前月份或禁用日期的颜色         | String | '#c0c4cc' | 否 |
| swipeStatus      | 外部传入的滑动控制，支持up,down,left,right        | String | '' | 否 |
| mainBackgroundColor      | 背景色        | String | '#0e8ee9' | 否 |
| visible          | 控制日历组件的显示或隐藏,需使用 `.sync` 修饰符                                                                                                        | Boolean  |     false      |    否    |
| scrollChangeDate | 控制滑动的时候是否修改选中的日期                                                                                                                      | Boolean  |      true      |    否    |
| model            | 日历组件以哪种形式展示。inline：内联的方式。dialog：弹窗的方式                                                                                        |  String  |     inline     |    否    |
| defaultDatetime  | 指定默认时间。                                                                                                                                        |   Date   |    当前时间    |    否    |
| format           | 确认日期时，回调事件返回的日期格式。如“YY/MM/DD hh:mm” 、“YY 年 MM 月第 DD 天，当前时间 hh 时 mm 分”、“MM DD,YY at hh:mm F”                           |  String  | YY/MM/DD hh:mm |    否    |
| weekStart        | 以星期几作为日历每一周的起始星期。可选['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday']                                  |  String  |     sunday     |    否    |
| pickerType       | 选择器类型 datetime：日期+时间 date：日期 time：时间                                                                                                  |  String  |    datetime    |    否    |
| showTodayButton  | 是否显示返回今日按钮                                                                                                                                  | Boolean  |      true      |    否    |
| isShowWeekView   | 是否以周视图展示组件                                                                                                                                  | Boolean  |     false      |    否    |
| disabledWeekView | 禁用周视图（设置为 true 后，无法上下滑动进行周/月切换）                                                                                               | Boolean  |     false      |    否    |
| disabledDate     | 设置日期的禁用状态，参数为当前日期，要求返回 Boolean （禁用该日期需返回 true）                                                                        | Function |      ---       |    否    |
| markDate         | 需要被标记的日期，可按不同颜色分组标记（不分组默认蓝色）。如：[{color: 'red',type: 'background', date: ['2019/02/25']},{color: 'blue', type: 'dot', date: ['2019/01/20']},'2019/03/20'] |  Array   |       []       |    否    |
| minuteStep       | 间隔时间。（分钟的步长）                                                                                                                              |  Number  |       1        |    否    |
| lang             | 选择的语言版本。可选值:['CN', 'EN']                                                                                                                   |  String  |       CN       |    否    |

# 事件

| 事件名称    | 说明                                                                                      | 参数                               |
| :---------- | :---------------------------------------------------------------------------------------- | :--------------------------------- |
| change      | 日期改变时，触发该事件。（返回的日期格式取决于 format 属性）                              | (date: 日期改变时，选中的日期)     |
| confirm     | 点击确认按钮时，触发该事件，dialog 模式中才有该按钮。（返回的日期格式取决于 format 属性） | (date: 点击确认按钮时，选中的日期) |
| click       | 点击日期时，触发该事件。（返回的日期格式取决于 format 属性）                              | (date: 当前点击的日期)             |
| touchstart  | 日历滑动 start 事件，同于原生该事件。                                                     | （event: touch 事件）              |
| touchmove   | 日历滑动 move 事件，同于原生该事件。                                                      | （event: touch 事件）              |
| touchend    | 日历滑动 end 事件，同于原生该事件。                                                       | （event: touch 事件）              |
| slidechange | 日历滑动的方向。返回值：right、left、up、down 。                                          | （direction: 滑动的方向）          |


## Other

- 在 dialog 模式中，如何显示日历组件？注意使用 `.sync` 修饰符

```
<vue-hash-calendar-slide :visible.sync="isShowCalendar"></vue-hash-calendar-slide>

//设置为true
this.isShowCalendar = true;
```

- 想要返回标准的英文格式日期，format 属性应该怎样写？ `MM DD,YY at hh:mm F`

```
<vue-hash-calendar-slide format="MM DD,YY at hh:mm F"></vue-hash-calendar-slide>

```

- 想要返回 12 小时制的日期，format 属性应该怎样写？ 在格式化字符串后面加上大写 `F`

```
<vue-hash-calendar-slide format="YY/MM/DD hh:mm F"></vue-hash-calendar-slide>

```

- 如何设置禁用日期？ 可参考源码中 `App.vue` 文件

```
// 例如禁用今日之后的所有日期

/** vue模板文件 **/
<vue-hash-calendar-slide :disabled-date="disabledDate"></vue-hash-calendar-slide>

/** vue methods 中的方法 **/
disabledDate(date) {
    let timestamp = date.getTime();
    if (timestamp > new Date().getTime()) {
        return true
    }

    return false
}
```

- 如果有其他问题， 或者功能上不兼容的。可以邮件沟通 allsmy.com@gmail.com，或者 github 提交 issue。
