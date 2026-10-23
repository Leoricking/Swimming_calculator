# 🏊 SwimLab — Swimming Training System

SwimLab 是一套可離線使用的游泳訓練分析與課表系統，核心目標是建立：

**測量 → 分析 → 找問題 → 技術訓練 → 主課 → Garmin 驗證 → 下一堂課**

目前版本：**SwimLab v3.0.1**

## ✨ 主要功能

- 游泳配速換算：25m / 50m / 100m / 200m / 400m / 800m / 1500m
- 泳力估算
- CSS / Critical Swimming Speed
- 多距離 Critical Speed 線性回歸
- 六區泳速
- 個人化課表產生
- 技術診斷
- Drill / 器材 Tag
- Garmin FIT / CSV 匯入
- 課表文字解析
- Garmin 智慧配對
- 訓練後分析
- 長期歷史與趨勢追蹤

---

## 1. 配速換算

輸入任一距離與成績，可換算對應：

- 25m
- 50m
- 100m
- 200m
- 400m
- 800m
- 1500m

可用於配速規劃、比賽預估與間歇目標設定。

---

## 2. CSS / 臨界泳速

### 400m / 200m CSS

公式：

```text
CSS = (T400 - T200) / 2
```

例如：

```text
400m = 6:05 = 365 秒
200m = 2:53 = 173 秒

CSS = (365 - 173) / 2
    = 96 秒 / 100m
    = 1:36 / 100m
```

### 多距離 Critical Speed

可輸入：

- 25m
- 50m
- 100m
- 200m
- 400m
- 800m
- 1500m

SwimLab 會以時間－距離線性回歸計算：

- Critical Speed（m/s）
- Critical Speed /100m 配速
- 回歸斜率
- 截距
- R²
- 與 400/200 CSS 的差異

用途是觀察泳者較偏：

- 速度型
- 耐力型
- 均衡型

---

## 3. 建議測試流程

### 測試前

- 前約 2 天避免高強度訓練
- 各距離盡量在同一週完成
- 比較不同週期時，盡量維持相似泳池與測試條件

### 可同日測試

- 25m
- 50m
- 100m
- 200m
- 400m

建議充分熱身後：

**先長距離 → 再短距離**

### 建議分日

- 800m
- 1500m

### 時間有限

可使用：

- 50m
- 100m
- 200m
- 400m

進行多點 Critical Speed 回歸。

---

## 4. 智慧課表產生

可依據：

- 訓練目標
- 泳力
- CSS
- 泳池長度
- 總距離
- 身體狀況
- 可用器材

產生包含：

- 暖身 Warm-up
- 技術 Technique
- Drill
- 器材訓練
- 器材 → 裸游轉換
- CSS
- Aerobic
- Sprint
- Butterfly
- Kick
- Recovery

的完整訓練課表。

---

## 5. 課表文字解析器

可直接貼自然語言課表，例如：

```text
200m 自暖身
+ 50m 自姿勢游泳*4
+ (50m 自(呼吸管 + Agility 划手板) + 50m 自裸游)*4
+ (100m 自裸游 1'40-1'45 + 休20s)*8
+ (200m 自 DMC 蛙鞋 + 休20s)*3
+ 50m DMC 蛙鞋蝶腳*4
+ 100m 緩
```

系統會解析：

- 距離
- 趟數
- 泳姿
- 目標配速
- 休息
- 器材
- Drill
- 訓練目的

---

## 6. 器材 Tag

支援例如：

- FINIS 呼吸管
- Agility Paddle
- MP Strength Paddle
- DMC Elite Max
- Zoomer Z2
- EDGE FIN
- Pull Buoy
- Kickboard
- 腰間挖水器

器材成績會與裸游分開判讀，避免把器材速度直接拿來和裸游比較。

---

## 7. Drill Tag

包含例如：

- 單臂划手
- 只踢水
- Scull
- 3-3-3
- Shark Drill
- 側身打水
- 6 Kick Switch
- 拳頭游
- Catch / Hold
- Body Dolphin
- 蝶式單臂
- 抬頭捷
- 划頻練習
- 均速練習
- 姿勢游泳 Technique Swim

Tag 說明頁會列出：

- 目的
- 原理
- 適用時機
- 常見錯誤
- 建議搭配

---

## 8. Garmin FIT 匯入

Garmin Swim 2 建議使用：

**Garmin Interval / Lap**

因為 Garmin Connect 的「間歇訓練」表格本身就是以 Lap / Interval 為主。

SwimLab 可匯入：

- 距離
- 時間
- 休息
- 划水數
- SWOLF
- 平均 HR
- 泳姿 / Drill 資訊

Length 則作為組內細節與泳姿判讀輔助。

---

## 9. Garmin CSV 匯入

支援 Garmin Connect 匯出的 CSV。

系統會嘗試：

- 辨識 Interval
- 分離休息資料
- 重建訓練組
- 保留配速與划水相關數據

若可取得 FIT，通常建議優先使用 FIT。

---

## 10. Garmin 智慧配對引擎

課表：

```text
50m × 4
```

Garmin：

```text
#5 = 50m
#6 = 50m
#7 = 50m
#8 = 50m
```

SwimLab 會辨識為同一個課表區塊。

同理可處理：

```text
100m × 8
200m × 3
```

智慧配對會考慮：

- 距離
- 趟數
- 順序
- 泳姿
- 休息
- 訓練結構

配對成功後可自動套用：

- 器材 Tag
- Drill Tag
- 訓練目的
- 目標配速
- 泳姿

Garmin 實測休息時間會被保留。

---

## 11. 訓練後分析

SwimLab 目前分析包含：

- 配速穩定度 Pace Stability
- 划水效率 Stroke Efficiency
- 技術耐力 Technique Durability
- 有氧效率 Aerobic Efficiency
- CSS 執行度 CSS Execution
- 器材 → 裸游轉換 Equipment → Naked Transfer
- 身體位置 / 踢腿 Body Position / Kick
- 整體訓練品質 Overall Session Quality

目標不是只給一個分數，而是回答：

- 哪裡進步
- 哪裡開始掉速
- 哪一段技術崩潰
- 器材能力有沒有轉移到裸游
- 下一堂應該練什麼

---

## 12. 器材 → 裸游轉換

例如：

```text
Agility 50m = 43 秒
裸游 50m    = 50 秒
```

數週後：

```text
Agility 50m = 43 秒
裸游 50m    = 47 秒
```

即使器材速度沒有變快，裸游已進步，表示：

- 抓水
- 水感
- 身體位置
- Timing
- 推進力

開始真正轉移到裸游。

---

## 13. 臨界速度訓練進階

核心原則：

**一次只調整一個變數。**

### 第一階段：增加趟數

```text
100m × 8
→ 100m × 10
→ 100m × 12
```

先維持配速與休息。

### 第二階段：縮短休息

例如：

```text
2:00 出發
→ 1:55 出發
```

保持游泳速度不變。

### 第三階段：增加距離

例如：

```text
100m 間歇
→ 200m 間歇
```

仍維持均速和技術品質。

### 第四階段：提高真正速度

耐力基礎穩定後再提高目標速度。

例如：

```text
1:40 /100m
→ 1:35 /100m
```

不要同時：

- 加速
- 加趟數
- 加距離
- 縮休息

---

## 14. 重新測試

建議約每：

**6–8 週**

重新測一次：

- CSS
- Critical Speed
- R²
- 短距離速度
- 中長距離表現
- Garmin 趨勢

只看 50m PB 並不足以代表整體泳力進步。

---

## 15. 長期訓練紀錄

SwimLab 使用瀏覽器本地儲存保存訓練資料，可追蹤：

- 配速
- CSS
- Critical Speed
- SWOLF
- 划水效率
- HR
- 器材轉換率
- 技術耐力
- Session Quality

目標是支援數十到上百次訓練的長期比較。

---

# 🧠 訓練理念

SwimLab 的核心不是單純堆訓練量，而是：

> **先把技術做對，再建立能長時間維持的速度。**

主要原則：

- 先減阻，再增加推進
- 維持穩定身體線
- 建立有效 Catch / Hold / Push
- 減少每划之間的掉速
- 改善身體滾轉
- 提高水感
- 器材訓練最後必須轉回裸游
- 速度、距離、趟數與休息逐步增加
- 用測量資料決定下一堂，而不是只憑感覺

---

# 🖥 使用方式

SwimLab 目前為單一 HTML 檔案。

不需要：

- Server
- Database
- 安裝程式

直接下載：

```text
SwimLab_Training_System_v3.0.1.html
```

以瀏覽器開啟即可。

建議：

- Google Chrome
- Microsoft Edge
- Opera
- Vivaldi

---

# 💾 資料儲存

訓練歷史目前儲存在瀏覽器 Local Storage。

注意：

- 清除網站資料可能會刪除紀錄
- 不同瀏覽器會有不同資料庫
- 長期使用建議定期備份

---

# 📁 Repository

```text
Swimming_calculator/
│
├── SwimLab_Training_System.html
├── README.md
└── ...
```

---

# 🛠 系統流程

```text
Workout Plan
    ↓
Garmin FIT / CSV
    ↓
Smart Matching
    ↓
Tag Reconstruction
    ↓
Training Analysis
    ↓
Long-Term Trend
    ↓
Next Workout
```

---

# 🚧 Future Development

預計持續改善：

- FIT parser
- 訓練歷史 Export / Import
- IndexedDB
- 長期趨勢圖
- Technique Breakdown Point 自動偵測
- CSS Compliance
- 自動進階課表
- 器材專項趨勢
- Butterfly 分析
- Triathlon swim 分析
- 手機版 UI
- 更多課表模板

---

# 📚 Knowledge Framework

SwimLab 將游泳教材中的概念轉成可執行工具，而不是逐字重製教材。

涵蓋：

- 水阻
- 身體線
- Catch / Hold / Push
- 水感
- 划距
- 划頻
- SWOLF
- 身體滾轉
- 踢腿
- 換氣
- 技術 Drill
- CSS / Critical Swimming Speed
- 速度耐力
- 間歇進階
- 重量與核心穩定

---

# ⚠ Disclaimer

SwimLab 是訓練輔助與數據分析工具。

實際課表仍應依：

- 技術狀況
- 疲勞
- 訓練年資
- 傷痛
- 泳池條件
- 教練回饋

進行調整。

若出現疼痛或異常不適，應降低強度或停止訓練。

---

# Version

```text
SwimLab v3.0.1
```

# Author

```text
Leoricking
```

GitHub repository:

```text
Swimming_calculator
```

# License

正式公開前可依需求加入：

- MIT
- Apache-2.0
- GPL-3.0
