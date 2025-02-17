# Swift GTD

一个给 RemNote 用的 GTD 插件。

## Tasks and Status 任务及其状态

There are five states of a task as follows:

任务共有以下五种状态：

- Scheduled
- Ready
- Now
- Done
- Cancelled

The state transition logic is as follows:

状态转换逻辑如下：

- Add a task and automatically toggle to the **Scheduled** state.
- A task is ready to be done (on the schedule), toggle it to **Ready** state.
- The ongoing task now should be in the **Now** state (only one task is allowed to be in the **Now** state).
- Finish a task and toggle to **Done** state.
- Give up a task and toggle to **Cancelled** state.


- 添加一个任务，自动转换到 Scheduled 状态。
- 准备处理一个任务（提上日程），将其转换到 Ready 状态。
- 现在手头正在做的任务应为 Now 状态（只允许有一个任务处于 Now 状态）。
- 完成一个任务，转换到 Done 状态。
- 放弃一个任务，转换到 Cancelled 状态。

The task status can be viewed via the hover widget located on the right side of the editor.

任务状况可通过位于编辑器右侧的悬浮微件查看：微件上的字母为任务状态的首字母。

<img width="503" alt="image" src="https://user-images.githubusercontent.com/38722307/181257157-6379c835-2fd1-49d0-ad29-19c943653b0b.png">

There are two ways to manually toggle status of a task:

有两种方法手动转换任务状态：

- Use commands (Accessed via Omnibar or slash menu, with the naming convention "Toogle + name of state to convert to").
- Use widget located on the right side of the editor.

- 使用指令（通过 Omnibar 或斜杠菜单触发，命名规则为 “Toogle + 要转换到的状态名”）。
- 使用位于编辑器右侧的悬浮微件。

  ![rn-indicator](https://user-images.githubusercontent.com/38722307/181256514-f9db4b5c-27af-4110-b26c-ff7265986f12.gif)

- Under "Task Overview" in the right sidebar panel, all tasks that are currently in Now, Ready and Scheduled states are listed, click on the task to jump to its rem.

右侧栏面板中 Task Overview 项下，会列出当前处于 Now，Ready 和 Scheduled 状态的所有任务，点击任务项即可跳转到其所在的 rem。

![rn-nav](https://user-images.githubusercontent.com/38722307/181257735-caf78927-94ba-4ad3-ba97-081fd1c16f9f.gif)

## Time Log

Swift-GTD will tracks each task status transition and automatically generates a timelog.

Swift-GTD 会追踪每个任务的状态变化，并自动生成 timelog。

![rn-timelog](https://user-images.githubusercontent.com/38722307/181259195-cb1fa2e0-725d-4eb2-8045-175891a873b3.gif)

You can attach a message to a timelog using *card syntax*. 

使用制卡语法，可以为一条 timelog 附上一条信息。

## Subtasks and Progress Bars 子任务与进度条

<img width="584" alt="image" src="https://user-images.githubusercontent.com/38722307/181260626-31193142-2a2a-4a63-89f4-75e50a45c539.png">

When adding / removing a subtask or toggle the status of a subtask, the progress bar of its parent task will be added / deleted / updated automatically.

当添加 / 删除子任务和更改子任务的状态时，会自动为父任务添加 / 删除 / 更新进度条。

Note: Currently, this plugin cannot capture changes to the task tree that are not generated by commands provided by the plugin (such as the new task command, etc.).

注意：目前此插件无法捕捉不经由插件提供的指令（如上面的 new task 指令等）产生的任务树更改。

For example, if you unindented a rem of a subtask, then the task is no longer part of its original parent task. However, the plugin cannot catch this event and will not automatically update the progress bar of the parent task.

比如：如果将某个子任务所在 rem 反缩进一级，则这个任务就不属于其原来的父任务了。但插件无法捕捉这一事件，也不会自动更新父任务的进度条。

When a progress bar error occurs due to this situation, you can use the "Update Focused Rem Tree Prgerss" command to fix.

当出现这种情况导致的进度条错误时，可以使用 Update Focused Rem Tree Prgerss 指令强制扫描当前 rem 所在 rem 树，修正进度条。

The progress bar style can be changed in the plugin settings.

进度条样式可在插件设置中更改。

If a task is tagged with "Automatically Done", the parent task will automatically toggle to the "Done" when all its subtasks are finished.

如果某个任务打上了 Automatically Done 标签，则当其所有子任务完成时，父任务会自动转换至完成状态。

![run-done](https://user-images.githubusercontent.com/38722307/181261912-94c51c5b-b581-4200-91d7-c21bf2656bf0.gif)

## 番茄钟

![rn-pomodoro](https://user-images.githubusercontent.com/38722307/181263143-0d75a17d-fc3d-4f0f-b3c5-89276845a6c8.gif)

点击右侧栏中飞镖即可打开番茄钟组件。输入番茄钟的时间，然后在想要完成的任务上使用 Start Pomodoro 指令即可启动一个番茄钟。

The time of the pomodoro is specified using the "x h x min x s" format, all the following inputs are legal.

番茄钟的持续时间使用 x h x min x s 格式指定，下面的输入都是合法的：

- 10min 20s
- 1h
- 1h10min7s
- 10 s

Starting the tomato clock will cause the corresponding task to toggle to the "Now". When the pomodoro finished, toggle to "Ready". This will update timelog too.

启动番茄钟会使对应任务切换到 Now 状态，番茄钟完成后切换到 Ready 状态。自动状态的切换和手工切换一样，会更新 Time Log 属性。

An unfinished pomodoro is not lost by closing the remnote tab/application. When you open Remnote, the plugin will automatically detect if there is a previously unfinished pomodoro and if so, continue.

一个未完成的番茄钟不会因为关掉 remnote 标签页 / 应用而丢失。在再次启动时，将会自动检测是否存在之前未完成的番茄钟，如果有，则继续。
