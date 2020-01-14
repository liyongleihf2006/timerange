# timerange
很简单的东西，就是做个整理,主要用在时间插件的快捷方式中

```js
console.log('昨天',getYesterday().toLocaleString());//昨天 2020/1/13 上午10:18:05
//昨天
function getYesterday(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    return new Date(time - baseUnit);
}
console.log('前天'+getTheDaybeforeYesterday().toLocaleString());//前天 2020/1/12 上午10:18:05
//前天
function getTheDaybeforeYesterday(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    return new Date(time - 2*baseUnit);
}
console.log('三天前'+getThreeDaysAgo().toLocaleString());//三天前 2020/1/11 上午10:18:05
//三天前
function getThreeDaysAgo(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    return new Date(time - 3*baseUnit);
}
console.log('一周前'+getAWeekAgo().toLocaleString());//一周前 2020/1/7 上午10:18:05
//一周前
function getAWeekAgo(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    return new Date(time - 7*baseUnit);
}
console.log('最近三天'+getThreeDays().map(day=>day.toLocaleString()));//最近三天2020/1/12 上午12:00:00,2020/1/14 上午10:33:29
//最近三天
function getThreeDays(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    var start = new Date(time - 2*baseUnit);
    start.setHours(0);
    start.setMinutes(0);
    start.setSeconds(0);
    start.setMilliseconds(0);
    return [start,d];
}
console.log('最近七天'+getSevenDays().map(day=>day.toLocaleString()));//最近七天2020/1/8 上午12:00:00,2020/1/14 上午10:33:29
//最近七天
function getSevenDays(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    var start = new Date(time - 6*baseUnit);
    start.setHours(0);
    start.setMinutes(0);
    start.setSeconds(0);
    start.setMilliseconds(0);
    return [start,d];
}
console.log('本周'+getCurrentWeek().map(day=>day.toLocaleString()));//本周2020/1/13 上午12:00:00,2020/1/14 上午10:33:29
//本周
function getCurrentWeek(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    var day = (d.getDay() + 6)%7;
    var start = new Date(time - day*baseUnit);
    start.setHours(0);
    start.setMinutes(0);
    start.setSeconds(0);
    start.setMilliseconds(0);
    return [start,d];
}
console.log('上周'+getPrevWeek().map(day=>day.toLocaleString()));//上周2020/1/6 上午12:00:00,2020/1/12 下午11:59:59
//上周
function getPrevWeek(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    var day = (d.getDay() + 6)%7;
    var end = new Date(time - (day+1)*baseUnit);
    end.setHours(23);
    end.setMinutes(59);
    end.setSeconds(59);
    end.setMilliseconds(999);
    var start = new Date(time - (day+7)*baseUnit);
    start.setHours(0);
    start.setMinutes(0);
    start.setSeconds(0);
    start.setMilliseconds(0);
    return [start,end];
}
console.log('本月'+getCurrentMonth().map(day=>day.toLocaleString()));//本月2020/1/1 上午12:00:00,2020/1/14 上午10:33:29
//本月
function getCurrentMonth(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    var date = d.getDate() - 1;
    var start = new Date(d.getTime()-date*baseUnit);
    start.setHours(0);
    start.setMinutes(0);
    start.setSeconds(0);
    start.setMilliseconds(0);
    return [start,d];
}
console.log('上月'+getPrevMonth().map(day=>day.toLocaleString()));//上月2019/12/1 上午12:00:00,2019/12/31 下午11:59:59
//上月
function getPrevMonth(){
    var baseUnit = 24*3600*1000;
    var d = new Date();
    var time = d.getTime();
    var date = d.getDate();
    var end = new Date(d.getTime()-date*baseUnit);
    end.setHours(23);
    end.setMinutes(59);
    end.setSeconds(59);
    end.setMilliseconds(999);
    var start = new Date(d.getTime()-date*baseUnit);
    start.setDate(1);
    start.setHours(0);
    start.setMinutes(0);
    start.setSeconds(0);
    start.setMilliseconds(0);
    return [start,end];
}
```
