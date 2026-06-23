# Sunny美髮首頁交接規格

## 專案概述

本專案為 Sunny美髮 單頁式首頁初版，使用 Bootstrap 5 本地檔案作為版面框架，並以自訂 CSS 管理品牌色、區塊間距、輪播、卡片、頁尾與互動樣式。

目前頁面檔案為 `index.html`，所有 CSS、JS、圖片資源都採用本地端引用，不使用 CDN。

## 技術與資源引用

- HTML 入口：`index.html`
- Bootstrap CSS：`css/bootstrap.min.css`
- 自訂 CSS：`css/style.css`
- Bootstrap JS：`js/bootstrap.bundle.min.js`
- 圖片與 SVG：`images/`

`index.html` 的 CSS 載入順序需維持如下，確保自訂樣式可以覆蓋 Bootstrap 預設樣式：

```html
<link href="css/bootstrap.min.css" rel="stylesheet">
<link href="css/style.css" rel="stylesheet">
```

頁尾前載入 Bootstrap bundle：

```html
<script src="js/bootstrap.bundle.min.js"></script>
```

## 目前頁面結構

頁面由上到下依序為：

1. 選單導覽列
2. 首頁輪播 Banner，5 張圖
3. 關於我們，左圖右文
4. 服務項目，4 張 Bootstrap card
5. 聯絡我們頁尾，含 logo、社群連結、公司資訊、版權宣告
6. 右下角回到頁首按鈕

## 導覽列錨點

- 首頁：`#top`
- 關於我們：`#about`
- 服務項目：`#services`
- 聯絡我們：`#contact`

新增區塊時，若要加入選單，請同步新增對應 `id` 與 `href="#..."`。

## 圖片配置

Logo：

- `images/ChatGPT Image 2026年6月15日 上午10_03_09.png`

輪播 Banner：

- 第 1 張：`images/engin_akyurt-hairdresser-4682901.jpg`
- 第 2 張：`images/engin_akyurt-hairdresser-4682950.jpg`
- 第 3 張：`images/jackmac34-hairdressing-4057094.jpg`
- 第 4 張：`images/jo_johnston-haircut-2664087.jpg`
- 第 5 張：`images/engin_akyurt-hairdresser-4639174.jpg`

關於我們：

- `images/jackmac34-hairdressing-4057094.jpg`

服務項目 cards：

- 電棒燙：`images/engin_akyurt-hairdresser-4682950.jpg`
- 質感染髮：`images/jackmac34-hairdressing-4057094.jpg`
- 深層護髮：`images/engin_akyurt-hairdresser-4639174.jpg`
- 精準剪裁：`images/jo_johnston-haircut-2664087.jpg`

社群圖示 SVG：

- Facebook：`images/facebook-brands-solid-full.svg`
- Instagram：`images/instagram-brands-solid-full.svg`
- TikTok：`images/tiktok-brands-solid-full.svg`

## CSS 維護規範

所有自訂樣式集中維護於 `css/style.css`，不要再把大量樣式寫回 `index.html` 的 `<style>` 標籤中。

主要樣式區塊：

- `:root`：品牌色與共用色票
- `.navbar`、`.brand-mark`、`.nav-link`：選單與 logo
- `.hero-carousel`、`.hero-caption`：輪播 Banner
- `.section-pad`、`.section-title`：共用區塊間距與標題
- `.about-img`、`.about-copy`：關於我們
- `.products`、`.product-card`：服務項目卡片區
- `.btn-brand`：橘色外框按鈕
- `.site-footer`、`.footer-mark`、`.social-link`：頁尾
- `.to-top`：回到頁首按鈕
- `@media (max-width: 767.98px)`：手機版調整

## 品牌樣式

目前主要品牌色定義於 `css/style.css`：

```css
:root {
  --brand-orange: #f56b00;
  --brand-ink: #29201d;
  --brand-paper: #fff9f7;
  --brand-soft: #f7efec;
}
```

若要調整整體色系，優先修改這些 CSS 變數。

## 按鈕樣式

`.btn-brand` 目前設計為：

- 白底
- 橘色文字
- 2px 橘色外框
- hover / active 時變為橘底白字

HTML 使用方式：

```html
<a href="#contact" class="btn btn-brand">詳細閱讀</a>
```

請保留 Bootstrap 的 `btn` class，並搭配自訂的 `btn-brand`。

## 新增服務項目方式

目前服務項目使用 Bootstrap grid：

```html
<div class="col-sm-6 col-lg-3">
  <article class="card product-card text-center">
    ...
  </article>
</div>
```

若維持 4 欄，使用 `col-sm-6 col-lg-3`。若增加到 6 項或 8 項，可直接複製 card 區塊，Bootstrap 會自動換行。

## 注意事項

- 本專案目前不依賴網路 CDN，請保持 CSS、JS、圖片路徑為本地端相對路徑。
- 若替換圖片，建議維持橫向比例，輪播與卡片目前透過 `object-fit: cover` 裁切。
- 圖片檔名若包含空白或中文仍可使用，但後續維護建議改成英文小寫與連字號命名，例如 `logo-scissors.png`。
- `images/circle-up-solid-full.svg` 目前尚未被使用；右下角回到頁首按鈕目前使用文字箭頭。
- 若新增更多頁面，請共同引用 `css/bootstrap.min.css`、`css/style.css`、`js/bootstrap.bundle.min.js`。
