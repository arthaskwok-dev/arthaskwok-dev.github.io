---
title: "DMX地址是甚麼？為甚麼兩盞燈會突然一起動？"
date: 2026-07-28 11:20:00 +0800
categories: [Trigo Book, Lighting Control]
tags: [DMX512, DMX地址, Fixture Mode, 香港中學禮堂]
description: "由DMX Universe、起始地址和燈具通道數，找出兩盞舞台燈同步動作及地址重疊的原因。"
---

> **讀者正在問：** 明明在控制台只選了一盞燈，為甚麼另一盞也會一起轉色、移動或閃動？  
> **文章承諾：** 看完你能理解 DMX 地址的排列方法，找出地址重疊和 Fixture Mode 不一致等常見問題。

DMX512 可以想像成一幢有 512 個信箱的樓宇。每個 **DMX Universe** 都有獨立的地址 001 至 512，控制台不停把數值送到這些位置；燈具則按自己的設定，讀取屬於它的那一段資料。

## 起始地址不是燈具的唯一通道

一盞簡單 Dimmer 可能只佔 1 個通道，但 Moving Head 可能需要 16、24 甚至更多通道。燈具設定的地址是 **Starting Address**，其後連續的地址會依照 Fixture Mode 分別控制 Pan、Tilt、Dimmer、Color、Gobo 等參數。

例如三盞燈都選用 8-channel Mode：

| 燈具 | 起始地址 | 實際佔用範圍 |
|---|---:|---:|
| Fixture 1 | 001 | 001-008 |
| Fixture 2 | 009 | 009-016 |
| Fixture 3 | 017 | 017-024 |

下一盞的起始地址，要放在上一盞佔用範圍之後。若燈具佔用 16 個通道，起始地址便可排成 001、017、033，而不是 001、002、003。

## 兩盞燈一起動的三個原因

### 兩盞燈設定了相同地址

若兩盞同型號、同 Mode 的燈都設定為 Universe 1／Address 001，它們會讀取同一組指令，因此完全同步。這可以是有意的鏡像控制，但兩盞燈便不能再獨立選擇。

### 地址範圍互相重疊

第一盞使用 001-016，第二盞卻由 010 開始，第二盞的部分參數便會誤讀第一盞的資料。結果未必是完全同步，也可能出現不合理的移動、轉色或頻閃。

### Fixture Mode 不一致

控台 Patch 使用 16-channel Profile，實體燈具卻設成 20-channel Mode，從某一通道開始，所有功能都會錯位。燈具型號相同也不夠，Mode 名稱和通道數必須一致。

## Universe 也屬於地址的一部分

Universe 1／Address 001 與 Universe 2／Address 001 是兩個不同位置，可以同時存在。故障排查時不要只說「它是 001」，而應完整記錄為 `U1/001`、`U2/001`。

## 安全排查次序

1. 把相關燈具 Dimmer 降至 0，停止正在運行的 Effect。
2. 核對每盞燈的 Universe、Starting Address 和 Fixture Mode。
3. 對照控台 Patch，確認 Profile 和 Mode 相同。
4. 逐盞選擇並短暫開至低亮度，不要一次把全組推至 Full。
5. 分別測試 Dimmer、Color、Pan 和 Tilt，確認沒有第二盞跟隨。
6. 把修正後地址更新到燈圖和 Patch 表。

地址不是貼在燈上的編號，也不是控台的 Fixture Number。它只是燈具在一個 DMX Universe 內接收資料的起點。

