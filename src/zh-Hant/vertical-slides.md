---
id: vertical-slides
title: 垂直幻燈片
layout: default
---

# 垂直幻燈片

你的幻燈片默認通過水平滑動過渡來逐步切換。這些水平幻燈片被視為你套件中的主要或*頂級*幻燈片。

你也可以在單個頂級幻燈片內嵌套多個幻燈片，以創建一個垂直堆疊。這是一種將內容在你的演示中邏輯分組的絕佳方式，並使包含可選幻燈片變得方便。

在演示時，你使用左/右箭頭來逐步瀏覽頂級（水平）幻燈片。當你到達一個垂直堆疊時，你可以選擇性地按上/下箭頭來查看垂直幻燈片，或者通過按右箭頭來跳過它們。以下是一個顯示此操作中的鳥瞰圖的範例。

<picture>
  <img src="https://static.slid.es/support/reveal.js-vertical-slides.gif" alt="帶有垂直幻燈片的幻燈片布局">
</picture>

## 標記

以下是一個簡單的垂直堆疊的標記範例。

```html
<section>水平幻燈片</section>
<section>
  <section>垂直幻燈片 1</section>
  <section>垂直幻燈片 2</section>
</section>
```

<div class="reveal reveal-example">
  <div class="slides">
    <section>水平幻燈片</section>
    <section>
      <section>垂直幻燈片 1</section>
      <section>垂直幻燈片 2</section>
    </section>
  </div>
</div>

## 導覽模式

你可以通過使用 `navigationMode` 配置選項來微調 reveal.js 的導覽行為。請注意，這些選項僅對使用水平和垂直幻燈片混合的簡報有用。以下是可用的導覽模式：

| 值      | 描述                                                                                                                                                                                                                                                                                                                                                                                                 |
| :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| default | 左/右箭頭鍵在水平幻燈片之間切換。上/下箭頭鍵在垂直幻燈片之間切換。空格鍵遍歷所有幻燈片（水平和垂直）。                                                                                                                                                                                                                                                                                               |
| linear  | 移除上/下箭頭。左/右箭頭遍歷所有幻燈片（水平和垂直）。                                                                                                                                                                                                                                                                                                                                               |
| grid    | 啟用此功能時，從一個垂直堆疊向相鄰的垂直堆疊向左/右步進時，將會導覽至相同的垂直索引處。<br><br>考慮一個套件，其中有六個幻燈片按兩個垂直堆疊排序：<br>`1.1`&nbsp;&nbsp;&nbsp;&nbsp;`2.1`<br>`1.2`&nbsp;&nbsp;&nbsp;&nbsp;`2.2`<br>`1.3`&nbsp;&nbsp;&nbsp;&nbsp;`2.3`<br><br>如果你在幻燈片 1.3 上並向右導覽，通常會從 1.3 往 2.1 移動。將 navigationMode 設置為 "grid"，相同的導覽會將你從 1.3 導覽到 2.3。 |