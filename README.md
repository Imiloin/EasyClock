# 工程实践与科技创新 Ⅱ-A 大作业

### 1. INIT 初始化

`INIT CLOCK` 指令初始化整个时钟，执行以下功能：

> 运行时间重置为 0
>
> 时间重置为 08:00:59
>
> 日期重置为 2023.06.11
>
> 闹钟时间重置为 09:00:00
>
> 秒表重置为 00:00:30，并停止运行
>
> 取消翻转显示，变为正向显示

此指令不会更改数码管的显示模式，例如若执行指令前数码管显示的是日期，执行后仍显示日期，但日期初始化为 2023.06.11 。若要修改显示模式，可使用按键 `SW1` - `SW4`  ，或使用 `RUN` 指令。

### 2. SET 设置

`SET TIME HH:MM:SS` 设置时间为 HH:MM:SS

`SET DATE YYYY.MM.DD` 设置日期为 YYYY.MM.DD

`SET ALARM HH:MM:SS` 设置闹钟时间为 HH:MM:SS

`SET STWATCH HH:MM:SS` 设置秒表倒计时为 HH:MM:SS (不会立即运行)

:warning: 输入 ":" 或 "." 时，请使用英文输入法 (ASCII 字符)

### 3. GET 状态获取

`GET RUNTIME` 获取当前运行时间（运行时间从初始化完成，即收到自定义字符后便会自动从 0 开始计时）

`GET TIME` 获取当前时间

`GET DATE` 获取当前日期

`GET ALARM` 获取当前闹钟时间

`GET STWATCH` 获取当前秒表时间

### 4. RUN 运行

`RUN RUNTIME` 数码管显示运行时间

`RUN TIME` 数码管显示当前时间

`RUN DATE` 数码管显示当前日期

`RUN ALARM` 在数码管上显示闹钟时间，并播放闹钟音乐

`RUN STWATCH` 在数码管上显示并运行倒计时秒表

### 5. REVERSE 翻转显示

`REVERSE` 指令翻转数码管显示，旋转板子 180 度可看到正常的显示内容，再次使用 `REVERSE` 可回归正常。

由于 7 段码的限制，小数点无法翻转，仍显示在原位置

### 6. SAVE 保存时间

`SAVE` 指令将当前时钟的日期和时间保存于 Flash 闪存中，断电后不会消失，可在断电前使用。当重新接电重启后，会载入 Flash 中存储的时间继续计时

### 7. 补充说明

输入 `?` 获取帮助信息，如
```
>> ?
You can use this as a terminal. Try command like "INIT", "SET", "GET", "RUN".
```

输入 `指令关键字` + `?` 可显示对应指令的帮助信息，如
```
>> SET ?
Set time, date, alarm or stopwatch, use "SET TIME HH:MM:SS" or "SET DATE YYYY.MM.DD" or "SET ALARM HH:MM:SS" or "SET STWATCH HH:MM:SS".
```

输入错误指令关键字会返回错误信息，如
```
>> INVCMD
Invalid command: INVCMD
You can use this as a terminal. Try command like "INIT", "SET", "GET", "RUN".
```

输入错误或不合法的指令参数会返回错误的参数并返回指令用法，如
```
>> SET DATE 2023.02.30  // 2月30日是非法的日期
Invalid argument-2 2023.02.30 for command SET
Set time, date, alarm or stopwatch, use "SET TIME HH:MM:SS" or "SET DATE YYYY.MM.DD" or "SET ALARM HH:MM:SS" or "SET STWATCH HH:MM:SS".
```

输入缺少或多余参数的指令会给出提示，如
```
>> GET  // 缺少参数
Empty argument-1 for command GET
Get runtime, time, date, alarmtime or stopwatch time, use "GET RUNTIME" or "GET TIME" or "GET DATE" or "GET ALARM" or "GET STWATCH".

>> RUN TIME XD  // 多余参数
Too many arguments for command RUN
Display runtime, time, date, alarmtime or stopwatch, use "RUN RUNTIME" or "RUN TIME" or "RUN DATE" or "RUN ALARM" or "RUN STWATCH".
```

指令中的字母不区分大小写，可以随意混用大小写

```
>> rUn ruNTimE
Display runtime!
```

指令有空格容错，多个空格会被当作一个空格处理
```
>> GET    STWATCH
Current stopwatch time is 00:00:30:00.
```

------

已上传至[传承·交大](https://share.dyweb.sjtu.cn/course/16799/)，可前往下载查看更详细的项目介绍

S800板大作业（2023）
