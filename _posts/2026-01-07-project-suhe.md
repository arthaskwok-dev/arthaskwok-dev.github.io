---
title: 【案例分析】光度平衡與空間構築：蘇淅公學 x 大灣區音樂節
date: 2026-01-07 10:00:00 +0800
categories: [Portfolio, Stage Lighting]
tags: [System Design, Color Theory, School Hall, Event Production]
image:
  path: /assets/img/suhe-concert.jpg
  alt: 蘇淅公學禮堂演出現場
---

> **Case Study 01:** 當高亮度的 LED 顯示屏介入傳統舞台時，燈光設計師如何解決「光比失衡」的物理難題？

## 1. 專案課題：有限空間內的「光學博弈」
 
**地點：** 蘇淅公學禮堂 (Kiangsu-Chekiang College Hall)
**場景：** 大灣區音樂節 (GBA Music Festival)

在學校禮堂這類非標準劇院空間 (Non-theatrical Space) 進行演出，最大的技術挑戰在於**「動態範圍 (Dynamic Range) 的控制」**。

本案中，舞台背景是一面高亮度的 LED Wall。在光學邏輯上，這是一個巨大的「自發光體」。如果缺乏精確計算，LED 牆的高流明輸出會直接導致前景燈光被「吞噬」，使表演者面部顯得黯淡，甚至造成攝影畫面的過曝與失真。

## 2. Trigo 的解題邏輯 (Engineering Logic)

針對此物理限制，我們採用了 **"Subtraction & Integration" (減法與融合)** 的設計哲學。

### 📐 色度連貫性 (Chromatic Coherence)
為了消除「螢幕」與「舞台」的割裂感，我們放棄了高對比的色彩碰撞，轉而採用 **Deep Blue (450nm-475nm 波段)** 的單色調美學。
* **理論基礎：** 藍色在視覺心理學上具有「後退感」。
* **實務應用：** 通過統一色溫，我們將 LED Wall 的高光與舞台的光束融為一體，創造出深邃的「無限景深」，打破了物理舞台的邊界限制。

### 📐 光束的幾何架構 (Volumetric Lighting)
光，在空氣中是不可見的，除非它遇到介質。
如現場照片所示，我們精密計算了光束燈 (Beam Fixtures) 的投射夾角。這些光束不再是隨意的掃描，而是作為**「隱形的柱子」**，在空中構建出幾何結構。這不僅增加了畫面的張力，更重要的是在視覺上引導了觀眾的焦點，使其集中在藝人身上，而非背後的螢幕。

### 📐 雜散光控制 (Spill Light Control)
工程與藝術的分野，在於對「暗部」的處理。
只有在 **Absolute Black (絕對黑)** 的基底上，光的能量才能被感知。我們嚴格限制了燈具的溢出光 (Spill Light)，確保非表演區域保持絕對黑暗。這種高對比度 (High Contrast Ratio) 的處理手法，是營造沈浸式氛圍的關鍵。

## 3. 結論 (Conclusion)

本案證明了，即使在受限的學校禮堂環境中，只要遵循嚴謹的光學邏輯與計算，依然能突破硬體天花板，創造出電視台轉播級別的視覺張力。

這就是 Trigo 所堅持的—— **Light is Art, Logic is Engineering.**

---
**Technical Data:**
* **Fixture:** Hybrid Moving Head / LED Profile
* **Protocol:** ArtNet / DMX512
* **System Integration:** Trigo System Engineering Limited
