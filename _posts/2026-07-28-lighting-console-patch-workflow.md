---
title: "甚麼是Patch？從燈具地址到控制台通道的完整流程"
date: 2026-07-28 11:57:00 +0800
categories: [Trigo Book, Lighting Control]
tags: [Patch, Fixture Profile, DMX512, 控制台]
description: "以香港中學禮堂為例，完整拆解燈具編號、Fixture Profile、Mode、DMX地址和控台Patch流程。"
---

> **讀者正在問：** 實體燈具已設定 DMX 地址，為甚麼控制台仍然控制不到，或者按 Dimmer 卻變成移動？  
> **文章承諾：** 看完你能由燈圖一路完成 Patch、逐項測試燈具，並建立可交接的 Patch 表。

Patch 是在控制台內建立一張翻譯表：告訴控台「Fixture 21 是哪一款燈、使用哪個 Mode，以及它在甚麼 Universe 和地址」。地址只是資料位置，Fixture Profile 才告訴控台每個通道代表甚麼功能。

## 五種資料不要混在一起

- **Fixture Number：** 操作員選燈時使用的編號，例如 21、22、23。
- **Fixture Type：** 燈具品牌和型號。
- **Fixture Profile：** 控台內對應該型號的參數定義。
- **Fixture Mode：** 燈具使用的通道配置，例如 Basic、Standard、Extended。
- **DMX位置：** 完整寫成 Universe／Starting Address，例如 `U2/101`。

Fixture Number 可以按燈桿或用途排列，不需要等於 DMX 地址。把台前燈編為 1-8、台後燈編為 11-18，通常比直接用地址選燈更易記。

## 完整Patch流程

### 1. 先定燈具編號

在燈圖上為每盞燈分配唯一編號，標明位置、型號和方向。全組人員應使用同一套編號，避免有人說「左邊第二盞」，另一人卻從相反方向數。

### 2. 選正確Fixture Profile和Mode

在控台資料庫選擇準確品牌、型號和 Mode。若找不到完全相同的 Profile，不要隨便選一款通道數相同的燈；通道次序不同，仍會控制錯誤。

### 3. 規劃Universe和地址

按每盞燈的 DMX Footprint 排列地址，避免重疊。把同一燈桿或同一資料線的燈放在有邏輯的 Universe，可令接線和故障排查更清楚。

### 4. 設定實體燈具

在燈具選單設定與計劃相同的 Universe、Address 和 Mode。修改後重新檢查畫面，不要只相信設定時按過的數字。

### 5. 在控制台完成Patch

輸入 Fixture Number、數量、Profile、Mode、Universe 和地址。先看控台有否報告地址重疊，再保存 Show File。

## 不要只用「全部Full」測試

逐盞測試才能發現重複地址。先在安全方向和 Dimmer 0 的狀態選擇單一燈具，再依次檢查：

1. **Dimmer：** 低亮度開關是否正確。
2. **Pan／Tilt：** 移動方向、範圍和 Home 位置是否合理。
3. **Color：** 基本顏色及白光是否對應。
4. **Gobo、Zoom等功能：** Profile 內的槽位是否吻合實體燈具。

測 Pan／Tilt 前要確認光束已關閉、舞台無人處於危險位置，亦沒有電線或障礙限制燈頭活動。

## Patch表最少記錄甚麼？

| Fixture | 位置 | 型號／Mode | Universe | 地址 | 備註 |
|---:|---|---|---:|---:|---|
| 21 | 上台左 | Wash／16ch | 1 | 101 | Pan Invert |
| 22 | 上台右 | Wash／16ch | 1 | 117 | 正常 |

每次更換燈具、Mode 或地址後，同步更新控台、燈圖和 Patch 表。真正可靠的 Patch 不只「現在控制到」，還要讓下一位操作員能夠看懂和重建。

