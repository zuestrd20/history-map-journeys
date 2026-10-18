# 歷史時空旅行社

給中學生的繁體中文互動歷史網站。從日常生活出發，以地圖、史料線索、證據選擇與小測驗探索秦、唐、宋。

## 旅程
- 宋代城市的一天：街市、河運與區域供應
- 秦整合：共同標準、行政與勞役成本
- 唐代旅行：城市、路網與文化交流

每課約10–15分鐘，附教師指南、投影模式及本機儲存的學習護照。無學生帳號、追蹤分析、排行榜或資料上傳。

## 使用與開發
網站為靜態HTML、CSS和JavaScript，成品位於 dist。可在本機啟動靜態HTTP伺服器預覽。

執行 `node test.cjs` 可驗證資料與主要互動流程（DOM fixture，不取代真實瀏覽器檢查）。GitHub Actions在main更新時執行測試並部署GitHub Pages。

## 史料與圖像
各課在網站底部列出博物館、大學與UNESCO來源。角色與情境是教學虛構。SVG地圖與插畫是原創概念示意，沒有精確疆界、比例尺或可導航古道；不以圖像代替完整社會史證據。

進度只保留在目前瀏覽器；可在旅人護照中清除。

## 3D 地球
Three.js 0.180.0 與 OrbitControls 以 MIT 授權隨站提供，授權檔在 dist/vendor。底圖為 Natural Earth 1:110m land（公有領域），來源 https://github.com/nvkelso/natural-earth-vector/blob/master/geojson/ne_110m_land.geojson 。底圖僅繪海岸線，不繪現代國界；歷史疆域為另行開關的教學示意層。所有資產同源載入，不依賴外部 CDN。

地球預設面向本課區域；拖曳、滾輪／雙指或鍵盤可達的控制按鈕可旋轉、縮放及重設。沒有自動旋轉、慣性或動畫，尊重減少動態的需求。WebGL2 或資產不可用時使用既有 2D 圖與文字線索。點位是現代約略座標；汴河網絡與江南為區域代表點。交通虛線和藍色河川為教學概念線，非測繪古道、精確古河道或行程。


## 歷史疆域比較
提供秦（參考圖約前220年）、唐／武周（700年主體統治區）、北宋時期、南宋時期及明（約1580年）五個切片。各切片可獨立選擇，切換旅程時回到對應朝代；關閉圖層不影響課程、測驗或進度。平面疆域圖與3D使用相同經緯度資料；原有不按比例的課程示意圖保留，兩圖不可直接疊合。

- 秦／唐／明參考：Library of Congress, *China: A Country Study*, Figure 2, printed page 12 (PDF page 60): https://tile.loc.gov/storage-services/master/frd/frdcstdy/ch/chinacountrystud00word/chinacountrystud00word.pdf#page=60
- 北宋／南宋地理關係參考：Columbia University, *The Song Dynasty and Its Rivals*: https://afe.easia.columbia.edu/songdynasty-module/outside-rivals.html 。來源圖片未重製，沒有宣稱圖示是精確1100／1200年疆界。
- `dist/territories.js` 為原創低精度教學輪廓，並非GIS資料。沒有使用CHGIS、沒有精確面積、沒有把都護府／羈縻／勢力範圍一律當作實際統治區。海岸邊緣以公有領域Natural Earth現代陸地裁切，僅供定位。
- 清代暫未收錄：參考圖分列本部、外部與勢力範圍，不能直接合成單一帝國色塊。尚未收錄其他朝代不表示不存在。
- 平面圖採相同經緯範圍（85–135°E，14–48°N），不是等積投影，不能由色塊面積計算平方公里。疆界因史料、時段與控制方式而異，不代表現代主權。

`npm test` 現有88項DOM／資料斷言，包含五切片、閉合輪廓、座標範圍、顯示開關、課程同步與獨立選圖；`npm run build` 更新同源Three.js bundle。這些檢查不能替代實際WebGL與行動裝置瀏覽器檢查。
