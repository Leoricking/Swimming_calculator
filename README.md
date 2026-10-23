# Swimming_calculator / SwimLab

SwimLab 是一套單一 HTML、可離線執行的游泳訓練分析與課表系統。

它把游泳成績、CSS、泳力、技術弱點、器材使用、Garmin 訓練資料與長期趨勢整合在同一個工具中，目標是讓每次訓練都能形成：

**測量 → 分析 → 找問題 → 課表 → 再測量**

目前版本：**v2.0.3**

---

## 主要功能

### 1. 配速換算

支援：

- 25m
- 50m
- 100m
- 200m
- 400m
- 800m
- 1500m
- 自訂距離

可使用：

- 距離 + 完成時間 → 換算 `/100m` 配速
- 距離 + 100m 配速 → 預估完成時間
- 任意距離 → 25 / 50 / 100 / 200 / 400 / 800 / 1500m 等速拆分

---

### 2. 泳力 / CSS

可輸入：

- 50m
- 100m
- 200m
- 400m
- 800m
- 1500m

系統可估算：

- 綜合泳力
- CSS
- 各距離對應能力
- Z1～Z6 訓練配速區間

CSS 計算：

```text
CSS = (400m 秒數 - 200m 秒數) / 2
```

---

### 3. 智慧課表產生器

依據：

- 目前 CSS
- 泳力
- 訓練目標
- 當日狀態
- 預計總量
- 可使用器材

自動組合課表。

支援方向：

- 1500m 自由式
- 自由式技術
- 裸游轉換
- 100m 蝶式
- 三鐵
- Sprint
- Recovery
- 自由潛水輔助

---

## 訓練分析

每次訓練可建立一個 Session。

可以自行輸入：

- 距離 / 趟
- 趟數
- 每趟成績
- 泳姿 / 類型
- 器材 Tag
- 分解動作 Tag
- 訓練目的
- 休息時間
- 划水數
- SWOLF
- 平均心率

例如：

```text
100m × 5

1:58
1:59
2:00
2:01
2:03
```

---

## 器材 Tag

支援多選：

- Agility
- MP Strength Paddle
- DMC Elite Max
- Zoomer Z2
- EDGE FIN
- FINIS 呼吸管
- 腰間挖水器
- Pull Buoy
- Kickboard
- 其他划手板
- 其他蛙鞋 / 腳蹼

---

## Drill Tag

包含：

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

---

## 訓練目的

採用中英雙語顯示：

- 技術 Technique
- 臨界泳速 CSS
- 有氧 Aerobic
- 衝刺 Sprint
- 恢復 Recovery
- 器材→裸游 Equipment→Naked
- 身體位置 Body Position
- 踢腿 Kick
- 抓水 Catch
- 換氣 Breathing
- 三鐵 Triathlon
- 蝶式 Butterfly
- 自潛 Freedive

---

## Garmin CSV / FIT

### CSV

支援 Garmin Connect CSV 匯入。

系統會嘗試辨識：

- Distance
- Time
- HR
- SWOLF
- Stroke Count
- Stroke Type

匯入後再補充器材 / Drill Tag 即可。

### FIT

v2.0.0 起內建離線 FIT parser。

可解析：

- Session
- Lap
- Length
- Distance
- Time
- Stroke Count
- Heart Rate
- Stroke Type
- Pool Length（若 FIT 有紀錄）

可選：

- Length 每趟匯入
- Lap 每組匯入
- Auto
- 排除休息 Length
- 匯入後先檢查或直接分析

> Garmin FIT 若只標示 `Drill`，通常無法知道實際是單臂、只踢水、Scull 等，因此仍需手動補 Drill Tag。

---

## 分析指標

### 配速穩定度 Pace Stability

比較前段與後段配速。

用於判斷：

- 前快後崩
- 技術耐力
- 配速控制

### 划水效率 Stroke Efficiency

整合：

- Pace
- Stroke Count
- DPS proxy

避免只看「游得快不快」。

### 技術耐力 Technique Durability

觀察疲勞後是否：

- 配速下降
- 划水數增加
- DPS 下降

### 有氧效率 Aerobic Efficiency

用：

```text
Pace + HR
```

觀察是否能做到：

> 更快的速度 + 相同或更低的心率

### CSS 執行品質 CSS Execution

分析 CSS 組中有多少趟落在目標範圍。

### 器材→裸游轉換 Equipment → Naked Transfer

比較相同距離：

```text
器材組 → 裸游組
```

用來追蹤：

- Agility → 裸游
- MP → 裸游
- DMC → 裸游
- 蛙鞋 → 裸游

### 身體位置／踢腿 Body Position / Kick

使用蛙鞋 → 裸游配對做趨勢參考。

---

## N/A 機制

v2.0.3 起：

**資料不足不再使用預設分數。**

例如：

- 沒 HR → Aerobic Efficiency 顯示 `N/A`
- 沒 CSS 組 → CSS Execution 顯示 `N/A`
- 沒器材→裸游配對 → Equipment Transfer 顯示 `N/A`

Overall Session Quality 只會平均真正可計算的指標。

---

## 長期趨勢

每次 Session 可儲存在瀏覽器中。

預設保留最近：

```text
200 Sessions
```

可查看：

- 最近 10 次
- 最近 30 次
- 最近 50 次
- 最近 100 次
- 最近 200 次

可追蹤：

- 裸游平均配速
- SWOLF
- DPS proxy
- Aerobic Efficiency
- CSS Execution
- Technique Durability
- Equipment → Naked Transfer
- Overall Session Quality
- 訓練總距離
- 器材使用分布
- Drill 使用分布
- 訓練目的分布

---

## 資料備份

資料主要儲存在瀏覽器 `localStorage`。

可使用：

```text
匯出備份 JSON
```

保存完整訓練歷史。

換電腦或瀏覽器後可再：

```text
匯入備份
```

還原 Session 與個人資料。

---

## 使用方式

### 本機

直接開啟：

```text
index.html
```

不需要：

- Python
- Node.js
- npm
- Server
- Database

---

## GitHub Pages

Repository：

```text
https://github.com/Leoricking/Swimming_calculator
```

若主檔名為：

```text
index.html
```

可使用 GitHub Pages 部署。

預期網址：

```text
https://leoricking.github.io/Swimming_calculator/
```

GitHub：

```text
Settings
→ Pages
→ Deploy from a branch
→ main
→ / (root)
```

---

## Project Structure

```text
Swimming_calculator/
├── index.html
├── README.md
└── commit_push.ps1
```

---

## Update

一般更新：

```powershell
git add .
git commit -m "Update SwimLab"
git push
```

或直接執行：

```powershell
.\commit_push.ps1
```

---

## Roadmap

後續可持續擴充：

- Garmin FIT parser 相容性
- Garmin / Suunto 自動資料匯入
- 每週 / 每月訓練量統計
- CSS 長期變化
- 100m / 400m / 1500m 成績預測
- Stroke Rate 與 DPS 分析
- 技術崩潰點自動偵測
- 訓練負荷與恢復分析
- 自動產生下一堂課
- 多裝置資料同步

---

## License

For personal training, research and development use.
