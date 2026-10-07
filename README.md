# GPX Run Route Analyzer · 跑步路線分析 (Built by Grok)

---

## English

Client-side web app for importing Apple Watch / workout **GPX** files, analysing splits, heart rate and elevation, and comparing multiple runs on the same route.

### Features

#### Import & multi-run
- Import one or more `.gpx` files (drag-and-drop or file picker)
- Tag function for grouping same/similar route(s)
- Overlay multiple tracks on one Leaflet map (colour-coded)
- Show / hide tracks and km markers per route
- Selected route: solid km markers; others: semi-transparent (toggle)
- Clear all loaded runs

#### Map (2D)
- OpenStreetMap base map
- Route polylines with **direction arrows**
- **1 km markers** on the map
- Click a loaded run in the sidebar to focus detail and map styling

#### Detail (single run)
- **Overview:** date, start time, distance, elapsed time, avg pace, point count, avg/max HR, elev gain/loss
- **Weather** (Open-Meteo hourly for the run window): average temperature, humidity, wind; source (ERA5 archive or forecast); approximate place name + grid coordinates
- **Heart rate distribution** (Karvonen zones)
  - Set **max HR** and **resting HR** in **Settings (⚙️)**
  - Zones: easy &lt;60% HRR · moderate 60–80% · hard &gt;80%
  - Percentage + time spent (`h:mm:ss`) per zone
  - HR vs distance chart
- **Elevation profile** (elevation vs distance; min/max markers)
- **Km splits table:** arrival time, pace, avg HR, elev change per km  
  - Time = when you reach that km; pace = duration of that km only

#### Compare
- Side-by-side summary table for visible runs
- Overlay charts: **pace / HR / elevation vs distance**
- Per-km pace comparison table
- **Export CSV**

#### 3D terrain route
- Path with optional **street / satellite** basemap (Esri tiles, no API key) or plain grid
- Start (green) / end (red) markers; numbered **km labels**
- **Elevation exaggeration** slider
- Camera modes: **Overview** (orbit) · **Follow cam** (third-person chase)
- **Timeline playback:** play/pause, scrubber, speeds 1× / 2× / 5× / 10× / 50× / 100×
- Semi-transparent white playback cursor
- HUD: current distance / total distance + elevation
- **Fullscreen** expand with controls at the bottom
- Expand button or short tap; Esc or Close to exit

#### Interface
- **Traditional Chinese / English** language switch (persisted)
- **Dark / light** theme (persisted)
- Settings modal: HR parameters + how to measure max / resting HR
- Fully client-side; no account required

### How to use

1. Export a workout as **GPX** (e.g. from Apple Watch via Health / export apps).
2. Open the app → **Import GPX** (multi-select allowed).
3. Use **Detail** for one run; **Compare** for overlays and CSV.
4. Open **⚙️ Settings** once to set max and resting HR for Karvonen zones.
5. Use **3D** for map-ground playback; **Expand** for fullscreen.

### Tech stack

| Piece | Choice |
|--------|--------|
| Map | Leaflet + polyline decorator |
| 3D | Three.js + OrbitControls |
| Charts | Canvas 2D |
| Weather | [Open-Meteo](https://open-meteo.com/) archive / forecast API |
| Place name | BigDataCloud reverse geocode (client) |
| 3D basemap | Esri World Street Map / World Imagery tiles |
| Deploy | Static files (e.g. Vercel) |

No build step: open or host `index.html`.

### Privacy

- GPX is parsed **only in your browser**.
- Weather and geocoding call public APIs with run time + approximate location.
- GRX uploaded reocrd and HR settings are stored in `IndexedDB` on this device only.

### Credits

- All lines written by Grok AI
- Map data © OpenStreetMap contributors (2D map)
- 3D basemap tiles © Esri and respective data providers
- Weather © Open-Meteo

---

## 中文

純前端單頁應用：匯入 Apple Watch／運動 **GPX**，分析分段、心率與海拔，並在地圖與 3D 視圖比較多次跑步。

### 功能

#### 匯入與多檔比較
- 匯入一個或多個 `.gpx`（拖放或選檔）
- 標籤功能,將相同/接近路徑跑步訓練結合, 以方便作出比較
- 多條路線疊加於同一 Leaflet 地圖（分色）
- 可顯示／隱藏各路線軌跡與公里標記
- 選中路線：實色公里標記；其他：半透明（可開關）
- 一鍵清除全部紀錄

#### 2D 地圖
- OpenStreetMap 底圖
- 路線折線＋**方向箭嘴**
- 地圖上的 **每公里標記**
- 在側欄點選紀錄以聚焦詳情與地圖樣式

#### 詳情（單一紀錄）
- **總覽：** 日期、開始時間、距離、經過時間、平均配速、軌跡點數、平均／最高心率、爬升／下降
- **天氣**（Open-Meteo 跑步時段小時資料）：平均氣溫、濕度、風速；資料來源（ERA5／預報）；大概地名＋網格座標
- **心率分佈**（Karvonen 公式）
  - 在 **設定 (⚙️)** 輸入最大心率與安靜心率
  - 區間：易 &lt;60% 心率儲備 · 中 60–80% · 高 &gt;80%
  - 各區百分比＋所佔時間（`h:mm:ss`）
  - 心率對距離圖
- **海拔剖面**（海拔對距離；最高／最低標記）
- **每公里分段表：** 到達時間、配速、平均心率、爬升變化  
  - 時間＝到達該公里的累計時間；配速＝該 1 公里用時

#### 比較
- 可見路線的並排總覽表
- 疊圖：配速／心率／海拔 對 距離
- 每公里配速比較表
- **匯出 CSV**

#### 3D 地形路線
- 路線＋可選 **街道／衛星** 底圖（Esri 圖磚，無需 API key）或純格網
- 起點（綠）／終點（紅）；帶數字的 **公里標記**
- **海拔誇張** 滑桿
- 視角：**俯瞰**（旋轉）· **跟隨視角**（第三人稱）
- **時間軸播放：** 播放／暫停、進度條、倍速 1×／2×／5×／10×／50×／100×
- 半透明白色播放點
- 左上角 HUD：當前距離／總距離＋海拔
- **全畫面**放大，底部保留控制列
- 放大按鈕或輕點進入；Esc 或關閉退出

#### 介面
- **繁體中文／英文** 切換（會記住）
- **深色／淺色** 主題（會記住）
- 設定：心率參數＋如何量度最大／安靜心率
- 全在瀏覽器執行；無需帳戶

### 使用方法

1. 將運動紀錄匯出為 **GPX**（例如 Apple Watch 經健康／匯出 App）。
2. 開啟應用 → **匯入 GPX**（可一次多選）。
3. 用 **詳情** 看單次；用 **比較** 看疊圖與 CSV。
4. 到 **⚙️ 設定** 填寫最大與安靜心率（設定一次即可）。
5. 在 **3D** 重溫路線；按 **放大** 全畫面播放。

### 技術

| 項目 | 選用 |
|------|------|
| 地圖 | Leaflet + polyline decorator |
| 3D | Three.js + OrbitControls |
| 圖表 | Canvas 2D |
| 天氣 | [Open-Meteo](https://open-meteo.com/) 歷史／預報 API |
| 地名 | BigDataCloud 反向地理編碼（客戶端） |
| 3D 底圖 | Esri World Street Map／World Imagery |
| 部署 | 靜態檔案（例如 Vercel） |

無需建置步驟：直接開啟或託管 `index.html`。

### 私隱

- GPX **只在你的瀏覽器** 內解析。
- 天氣／地理編碼會呼叫公開 API，並傳送跑步時間與大概位置。
- 上傳之GPX文件及心率設定只以`IndexedDB`形式儲存在本機 。

### 已知限制

- 消費級 GPS 海拔在平路可能雜訊較大。
- Open-Meteo 天氣是 **小時級模式網格**，不是香港天文台站名。
- 3D「地圖」是軌跡下的 **平面圖磚**，不是完整 3D 建築或地形模型。
- 圖磚供應商可能限流；**格網** 底圖不依賴圖磚。

### 致謝

- 全部程式碼以Grok AI編寫
- 地圖資料 © OpenStreetMap 貢獻者（2D 地圖）
- 3D 底圖圖磚 © Esri 及相關資料提供者
- 天氣資料 © Open-Meteo
