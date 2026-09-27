# GPX 跑步路線分析

匯入 Apple Watch / WorkoutGPX / HealthFit 匯出嘅 GPX，喺地圖上分析同比較多次跑步。

## 功能

- 匯入單一或多個 GPX
- 地圖路線疊加比較
- 每公里分段（到達時間、配速、心率、爬升）
- 心率曲線同分佈
- 多檔總覽／配速／心率比較

## 部署到 Vercel

### 方法一：網頁拖放（最快）

1. 去 [vercel.com](https://vercel.com) 登入（可用 GitHub）
2. 撳 **Add New… → Project**
3. 選擇 **Upload** / 拖呢個資料夾上去
4. 撳 Deploy

### 方法二：Vercel CLI

```bash
npm i -g vercel
cd gpx-run-analyzer-deploy
vercel
```

跟住終端機提示登入同確認即可。

### 方法三：GitHub

1. 將呢個資料夾 push 去 GitHub repo
2. 喺 Vercel 撳 **Import** 該 repo
3. Framework Preset 選 **Other**，直接 Deploy

部署完成後會得到一個 `https://xxx.vercel.app` 網址，用手機瀏覽器打開即可匯入 GPX。
