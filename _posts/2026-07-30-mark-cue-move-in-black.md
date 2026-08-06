---
title: "甚麼是Mark Cue？如何避免搖頭燈在亮着時掃過觀眾？"
date: 2026-07-30 17:30:00 +0800
categories: [Trigo Book, Lighting Programming]
tags: [Mark Cue, Move In Black, Moving Head, Cue]
description: "利用Mark Cue在暗中預置位置、顏色和Gobo，避免搖頭燈亮着移動及掃過禮堂觀眾席。"
---

> **讀者正在問：** 下一個 Cue 只想讓搖頭燈在新位置亮起，為甚麼它會一邊亮、一邊由舞台掃過觀眾席？  
> **文章承諾：** 看完你能用 Mark Cue 或 Move in Black，按正確次序預置位置、顏色和 Gobo，並知道自動 Mark 仍要檢查甚麼。

Mark Cue 又叫 Setup Cue，表面上可能甚麼也沒有發生，實際工作是趁燈具亮度為零時，先把非亮度參數移到下一個畫面需要的狀態。

## 問題出在動作次序

假設 Cue 5 的搖頭燈在台右淡出，Cue 6 要它在台左亮起。若 Cue 6 同時發出 Position 和 Intensity 指令，燈具便可能在光束已開啟時移動，於是整條移動路徑都被觀眾看見。

較乾淨的次序是：

1. Cue 5 先把燈具 Intensity 降至 0。
2. Cue 5.5 在黑暗中移到台左，並預先轉好 Color、Gobo、Zoom 等參數。
3. 確認所有機械動作完成。
4. Cue 6 只把 Intensity 淡入。

如此觀眾只會看見完成後的光區，不會看見搬運光束的過程。

## 手動Mark怎樣做？

建立一個位於淡出 Cue 與下一個亮起 Cue 之間的小數 Cue，例如 5.5，為需要預置的燈具寫入：

- Intensity = 0
- 下一個 Cue 的 Position
- 下一個 Cue 的 Color、Gobo、Prism、Zoom 或 Focus
- 足夠完成移動和轉輪的時間

可把 Cue 命名為 `MARK`，並使用一致的編號規則，方便其他操作員辨認。安靜場景亦要考慮燈具移動、風扇和轉輪噪音；最快完成不一定最合適。

## 自動Mark不是完全自動安全

部分控台提供 Auto Mark 或 Move in Black，會找出由 0% 亮度轉為有光的燈具，提前準備非亮度參數。它很有效率，但仍可能有以下限制：

- 未把外接換色器或特殊參數視為可 Mark 項目。
- Mark 時間不足，燈頭尚未到位便開始淡入。
- 另一條 Playback 或 Effect 仍把燈具保持在有光狀態。
- 設計本來想看見移動，Auto Mark 卻把動作藏起來。

## 一定要檢查上一個Cue

Mark 能否在黑暗中進行，取決於燈具在**上一個狀態真的已經熄滅**。排練時不要只由 Mark Cue 開始測試，應至少由前一個有光 Cue 完整播放到下一個有光 Cue。

同時由觀眾席、兩側座位和攝影機方向檢查。若光束仍會掃過觀眾，先修正 Intensity 與 Position 的次序、停止其他 Playback，並重新安排移動路徑；不要靠把 Fade 加快來掩飾。

