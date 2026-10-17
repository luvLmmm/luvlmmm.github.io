<div align="center">

<sub>T H E &nbsp;&nbsp; F R O N T &nbsp;&nbsp; P A G E</sub>

# 头版

**每天早上 6 点，为你印好今天的报纸。**

**[阅读今日头版 →](https://raemyn24.github.io/)**

![每日更新](https://img.shields.io/badge/每日更新-06:00_CST-191919?style=flat-square)
![全文编译](https://img.shields.io/badge/全文编译-27_篇-4d4d4d?style=flat-square)
![八个版块](https://img.shields.io/badge/八个版块-各_3_篇-6f6f6f?style=flat-square)

</div>

---

<p align="center"><sub>1 头条 &nbsp;·&nbsp; 2 次条 &nbsp;·&nbsp; 8 个版块 × 3 &nbsp;·&nbsp; 共 27 篇站内全文</sub></p>

---

## 这是什么

头版是一份自动出版的中文新闻简报，放在 GitHub Pages 上。每天北京时间早上 6 点出一期。稿子来自读过的公开报道，用自己的话重写；事实、数字和引语留在那一篇原文里。

一期 **27** 篇站内编译全文：1 条头条、2 条次条，加上八个版块各 3 篇。头条和次条是版块之外的故事。首页标题点进编译页，文末「原文 ↗」回到原来的网站，页内也可以回到头版对应的版块。每篇是一段导语加上 5–9 段正文，直接引语译成中文。

## 八个版块

<table>
  <tr>
    <td align="center"><strong>01 · 国际</strong><br><sub>WORLD · 3</sub></td>
    <td align="center"><strong>02 · 经济</strong><br><sub>ECONOMY · 3</sub></td>
    <td align="center"><strong>03 · 政治</strong><br><sub>POLITICS · 3</sub></td>
    <td align="center"><strong>04 · 科技</strong><br><sub>TECH · 3</sub></td>
  </tr>
  <tr>
    <td align="center"><strong>05 · AI 产业</strong><br><sub>AI INDUSTRY · 3</sub></td>
    <td align="center"><strong>06 · 芯片</strong><br><sub>CHIPS · 3</sub></td>
    <td align="center"><strong>07 · 美股</strong><br><sub>US STOCKS · 3</sub></td>
    <td align="center"><strong>08 · Web3</strong><br><sub>WEB3 · 3</sub></td>
  </tr>
</table>

## 行情

页顶一条黑底滚动条，滚的是加密价格。文末「市场」默认折起，先露出常用市场的前两行，点开才是三张完整的表。

数字在读者自己的浏览器里刷新。每一组两个来源同时问，谁先成功用谁。东方财富、腾讯和 OKX 在大陆可以直接打开。都失败就读仓库里的 JSON，JSON 也失败就用写在页面里的备用数字。

| 栏目 | 品种 | 实时来源 | 失败时 |
|---|---|---|---|
| 常用市场 COMMON | 黄金、白银、布伦特、美元/人民币 | 东方财富 / 腾讯 | `common-quotes.json` |
| 加密 CRYPTO | BTC、ETH、SOL、XRP、DOGE | Coinbase / OKX | `crypto-quotes.json` |
| 美股 US STOCKS | NVDA、AAPL、MSFT、AVGO、AMD、TSM、MU、INTC、META、GOOGL、AMZN、ARM | 东方财富 / 腾讯 | `us-quotes.json` |

加密大约每 10 秒拉一次，常用市场和美股大约每 5 分钟。从别的标签页回到报纸上时，会马上再刷新。

## 版式

版心按一张黑白报纸来排。纸白 `#f6f6f4`，墨黑 `#191919`，其余是灰。标题用宋体。版块编号是黑底白字。报头下面的日期行，上下各一道细线。

打开站点先是一屏锁住的欢迎页：竖排「头版」，上面一行 THE FRONT PAGE 跟着打字机光标。封面写着「为你筛选值得读的新闻 / 每天一页读完」，以及「8 个版面 · 24 篇报道」——这 24 篇是八个版块；头条和次条在这个数字之外。底部期次每天更换：`本期 MM-DD 已更新`，英文一行 `EDITION MM-DD READY`。

配图只留本地 WebP，放在 `img/日期/` 里，页面上呈灰度。拿不到干净、允许随报道使用的原图时，这一则就不配图。

## 出刊

- 每天 **06:00（北京时间，Asia/Shanghai）** 自动搜集、编译、配图、发布
- 代码由 [`raemyn24-bot`](https://github.com/raemyn24-bot) 推送
- 下一期怎么印、哪些地方不能改，写在 [PUBLISHING.md](PUBLISHING.md)

署名与网站页脚相同：由 Grok Bot 自动采编、排版与更新。

---

<div align="center">

新闻与行情来自公开网络来源和公开接口，仅供参考，可能有延迟或误差，不构成任何投资建议。

<sub>© 2026 头版 · 由 Grok Bot 自动采编、排版与更新</sub>

</div>
