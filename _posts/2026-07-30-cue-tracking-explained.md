---
title: "Cue和Tracking怎樣運作？為甚麼上一個效果會留到下一個Cue？"
date: 2026-07-30 09:08:00 +0800
categories: [Trigo Book, Lighting Programming]
tags: [Cue, Tracking, Block Cue, 控台編程]
description: "拆解Tracking控台如何只記錄參數變化，以及上一個顏色、位置或Effect殘留到下一個Cue的原因。"
---

> **讀者正在問：** 已經寫了下一個 Cue，為甚麼上一幕的藍色、Gobo 或動態 Effect 還留在舞台上？  
> **文章承諾：** 看完你能分辨 Cue 狀態與參數指令，理解 Tracking、非 Tracking 和 Block Cue，並安全修正殘留資料。

很多人把 Cue 想成一張完整燈光照片。Tracking 控台的思路卻更像一串修改指令：**沒有在新 Cue 改變的參數，會保留上一個有效數值。**

## Cue記錄的是哪些資料？

假設 Cue 1 把 Fixture 21 設為紅色、50% 亮度；Cue 2 只修改 Position。進入 Cue 2 時，燈會移到新位置，但仍然保持紅色和 50%，因為 Cue 2 沒有給 Color 和 Intensity 新指令。

這不一定是錯誤。Tracking 能避免每個 Cue 重複儲存相同數值，亦可讓一次修改自然延續到後面的場景。

## Tracking與非Tracking的分別

- **Tracking控制：** Cue 主要記錄改變過的參數，未改變的數值由之前一路流入。
- **非Tracking控制：** 每個 Cue 傾向保存當時所有參數的完整狀態，Cue 之間較獨立，但重複資料較多。

不同控台還有 Cue Only、Track Forward、Update、Assert 等功能。名稱和細節會變，但核心問題都是：這次修改只屬於當前 Cue，還是應沿着後續 Cue 繼續？

## 常見殘留問題

- 上一個 Cue 啟動了 Position 或 Intensity Effect，下一個 Cue 沒有停止它。
- 顏色在 Cue 5 設為藍色，直到 Cue 12 都沒有新 Color 指令。
- 另一條 Cuelist、Executor 或 Playback 仍在控制同一參數。
- 修改前段 Cue 時選了 Track Forward，結果改動流入多個後續 Cue。
- 以為 Blackout 會清除所有資料；其實它可能只把亮度壓到零，位置、顏色和 Effect 狀態仍存在。

## Block Cue是甚麼？

Block Cue 為指定燈具寫入完整參數，阻止較早的數值穿過這個界線。香港中學舞蹈表演可在每個節目開首建立 Block Cue，避免上一隊的顏色或 Effect 影響下一隊。

但不要把每個 Cue 都 Block。過度阻擋會失去 Tracking 的優點，亦令前段修改無法自然更新後續畫面。

## 安全修正流程

1. 修改前先另存新版本，保留上一個可用 Show File。
2. 重播出問題的前一個 Cue 和當前 Cue，確認殘留由哪一步開始。
3. 查看 Cue 內容或 Tracking Sheet，找出參數的原始來源。
4. 若數值本應由前段延續，修改來源 Cue；若只改當前畫面，使用 Cue Only 或控台等效功能。
5. 明確停止不再需要的 Effect、Playback 或 Cuelist。
6. 只在節目段落邊界加入必要的 Block Cue，再從更早的 Cue 完整重播測試。

不要看到殘留便在每個 Cue 寫一個零。先找出資料從哪裏 Track 過來，才不會修好這一幕、同時破壞後面十幕。

