# Home, A–Z — A Dictionary of Home

一個 30 天海報專案的作品集網站（純 HTML / CSS 靜態網站，不需要安裝任何東西，可直接放到 GitHub Pages）。
A static portfolio site (plain HTML + CSS, no build step) for a 30-day poster project. It treats each poster as an entry in a dictionary that tries to define "home".

網站共 3 頁：**首頁**、**專案／字典頁**、**關於我**。
風格參考作者自己的海報：小孩蠟筆畫的紅、藍、黃、綠、粉，粗黑邊，皺褶紙張質感。

## 資料夾結構 / Folder map

```
.
├── index.html            首頁 Home
├── dictionary.html       專案與字典 The Dictionary (10 entries + 30-day grid)
├── about.html            關於我 About
├── css/style.css         共用樣式（顏色、紙張質感 class、貼紙字）
├── images/
│   ├── posters/          網頁用海報圖（720 px 寬，已壓縮）
│   └── textures/         5 張紙張質感圖（從作者海報邊緣裁切、鏡像拼接）
├── content/entries.json  字典條目與章節文字（資料版）
├── .nojekyll             讓 GitHub Pages 原樣提供檔案
├── AGENTS.md             給 AI 寫程式工具／協作者的工作規則
└── handoff/
    ├── DESIGN_SPEC.md    完整設計規格（色票、字型、版面、元件、內容、已知問題）
    └── previews/         三頁的設計預覽圖（1440 px 桌面版）
```

## 預覽 / Preview locally

直接用瀏覽器開 `index.html` 就能看。若要用本機伺服器：

```
python3 -m http.server 8000
# 然後開 http://localhost:8000
```

字型（Archivo Black、Gochi Hand、Space Grotesk）從 Google Fonts 載入，預覽時需要網路。

## 放上 GitHub Pages / Deploy

1. 在 GitHub 建立新 repository（例如 `home-az`），把這個資料夾的**全部內容**上傳到 repository 根目錄（`index.html` 要在根目錄）。
2. 進入該 repository 頁面 → 上方分頁 **Settings** → 左側選單 **Pages** → 在 **Build and deployment** 區塊，**Source** 選 **Deploy from a branch**。
3. 在 **Branch** 選 `main`，旁邊的資料夾選 **/ (root)**，按 **Save**。
4. 等一到兩分鐘，頁面上方會出現網址（通常是 `https://<你的帳號>.github.io/home-az/`）。

網站內所有連結和圖片都是相對路徑，放在 `https://<帳號>.github.io/<repo>/` 這種子路徑底下也能正常運作。

## 上線前要替換的內容 / Placeholders to fill in

網站裡有這些中括號占位文字，請換成真實資料（尚未提供）：

| 占位文字 | 出現位置 |
| --- | --- |
| `[YOUR NAME]` | 三頁的頁尾；About 的標題 |
| `[YOUR EMAIL]` | 三頁的頁尾；About 的聯絡區 |
| `[YOUR INSTAGRAM]`、`[YOUR PORTFOLIO LINK]` | About 的聯絡區 |
| `[YOUR PHOTO]` | About 的左側相框（換成 `<img>`） |
| `[YOUR OWN NOTE ABOUT WHY HOME MATTERS TO YOU]` | About 的 "Why a dictionary of home?" 段落 |

用這個指令可以一次找出全部：`grep -n "\[YOUR" *.html`

另外，`dictionary.html` 底部的「30 天」方格只有 Day 9–12 有縮圖，其他天數目前只有數字，等其他海報完成後再補。

## 已知注意事項 / Notes

- 海報 Day 10（`images/posters/day10-address.jpg`）圖片裡的文字寫成 "Adress"（少一個 d）。網頁文字使用正確拼法 "address"，圖片本身沒有改動。
- 版面以桌面版 1440 px 為主，窄螢幕只做到自動換行，沒有另外設計手機版。
- 更多細節見 `handoff/DESIGN_SPEC.md`。
