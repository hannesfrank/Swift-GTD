# Swift GTD

一个给 RemNote 用的 GTD 插件。

## 任务及其状态

![swift-gtd2](https://user-images.githubusercontent.com/38722307/179881874-b2deca60-8659-4db4-98f9-06d931f14839.gif)

任务共有以下五种状态：

- Scheduled
- Ready
- Now
- Done
- Cancelled

状态转换逻辑如下：

- 添加一个任务，自动转换到 Scheduled 状态。
- 准备处理一个任务（提上日程），将其转换到 Ready 状态。
- 现在手头正在做的任务应为 Now 状态（只允许有一个任务处于 Now 状态）。
- 完成一个任务，转换到 Done 状态。
- 放弃一个任务，转换到 Cancelled 状态。

所有状态转换及其时间都会记录在 Time Log 这个属性里。

## 子任务与进度条

当添加子任务和更改子任务的状态时，会自动为父任务添加、删除、更新进度条。

注意：目前此插件无法捕捉不经由插件提供的指令（如上面的 new task 指令等）产生的任务树更改。

比如：如果将某个子任务所在 rem 反缩进一级，则这个任务就不属于其原来的父任务了。但插件无法捕捉这一事件，也不会自动更新父任务的进度条。

当出现这种情况导致的进度条错误时，可以使用 Update Focused Rem Tree Prgerss 指令强制扫描当前 rem 所在 rem 树，修正进度条。

进度条样式可在插件设置中更改。

## 番茄钟

![swift-gtd](https://user-images.githubusercontent.com/38722307/179881363-1e36329b-f94d-47f5-93f7-741e48156425.gif)


点击右侧栏中飞镖即可打开番茄钟组件。输入番茄钟的时间，然后在想要完成的任务上使用 Start Pomodoro 指令即可启动一个番茄钟。

番茄钟的时间使用 x h x min xs 格式指定，下面的输入都是合法的：

- 10min 20s
- 1h
- 1h10min7s
- 10 s

启动番茄钟会使对应任务切换到 Now 状态，番茄钟完成后切换到 Ready 状态。自动状态的切换和手工切换一样，会记录到 Time Log 属性中。

一个未完成的番茄钟不会因为关掉 remnote 标签页 / 应用而丢失。在再次启动时，将会自动检测是否存在之前未完成的番茄钟，如果有，则继续。

## 未来计划

- 侧栏提供按钮，点击即可执行指令
- 番茄钟支持休息
- 番茄钟支持提醒
- 支持计算一个任务的总用时
- 支持以图表的形式做时间分析
