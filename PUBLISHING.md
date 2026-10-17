# 头版出版手册

给下一次自动出版用。只靠这份说明，就应该能做出新的一期，而不用再猜版式。

报纸是静态 GitHub Pages。版式已经定死。每天只换新闻、日期和行情数字。

## 每天必须遵守的规则

1. **不改版式、样式和结构。** `index.html` 里的 `<style>` 整段保持不动。欢迎页 `#welcome` 的 DOM、class、按钮和排版保持不动。不要改日期脚本、折叠和行情滚动：`#dateline-date` 和 `#w-date` 仍由读者浏览器的本地日期覆盖。轮询保持加密 10 秒、常用市场和美股 5 分钟，外加 `visibilitychange`。实时来源按下面「行情」一节，不要改回只读 JSON。允许改的只有：欢迎页期次、两处署名的文字、日期的静态初值、`<!-- HERO -->` 到 `<!-- 市场 -->` 之间的新闻、三份行情 JSON、脚本里的 `FALLBACK`、`CM_FALLBACK`、`US_FALLBACK` 数字和备用时间标签，以及行情一节写明的取数地址。
2. **头条和次条不与版块重复。** 1 条头条 + 2 条次条，必须是另外 24 条版块稿以外的故事。英雄位和八个版块之间，不得把同一事件写成两篇。相关但角度不同的稿可以并存（例如一条写信用利差，另一条写当日股价；一条写价格，另一条写 ETF 资金流），标题和正文重点必须不同。
3. **配图只留本地 WebP。** 放在 `img/YYYY-MM-DD/`。没有干净、允许使用的原图就删掉 `figure`，不要外链，不要用带出版方水印或叠字的图。
4. **欢迎页期次每天改成这一期的日期。** 两处 span 都改：`本期 <span id="w-ed">MM-DD</span> 已更新` 和 `EDITION <span id="w-ed-en">MM-DD</span> READY`。只改文字，不改标签。
5. **两处署名都是 Grok Bot，文字相同，标记不动。** 欢迎页是 `<span class="tm">由 Grok Bot 自动采编、排版与更新</span><span class="en tm">AUTOMATED BY GROK BOT</span>`。页脚是 `<span class="credit">由 Grok Bot 自动采编、排版与更新<br/>AUTOMATED BY GROK BOT</span>`。文章页、README 如果出现同样的采编署名，也改成 Grok Bot。新闻里合法的产品名不要改，例如 Meta 的 Muse、Muse Spark、Muse Spark Open。

## 一期是什么

- 日期用北京时间。报纸日期行写成 `2026年10月18日 星期日` 这种格式。
- 新闻窗口大约是出版前 24–48 小时。上一期没赶上、而这期仍是最新进展的稿可以用。不要把上一期已经写过的故事再写一遍，除非有真正的新进展。
- 共 27 篇，全部是站内中文编译页：
  - 头条 1
  - 次条 2
  - 国际、经济、政治、科技、AI 产业、芯片、美股、WEB3 各 3
- 每篇都基于一篇真正读过的公开报道。用自己的话重写。事实、数字、引语、背景保留。直接引语译成中文。不编造。一篇正文只对一篇原文负责；没读过的第二来源里的数字不要混进去。

## 文件

| 路径 | 作用 |
|---|---|
| `index.html` | 首页。一天只改上面第 1 条允许改的部分 |
| `articles/YYYY-MM-DD/slug.html` | 当天 27 篇编译。旧日期目录留着 |
| `img/YYYY-MM-DD/name.webp` | 当天配图。旧日期目录留着 |
| `common-quotes.json` | 黄金、白银、布伦特、美元/人民币 |
| `crypto-quotes.json` | BTC ETH SOL XRP DOGE |
| `us-quotes.json` | 美股收盘。不含 SNDK |
| `PUBLISHING.md` | 本手册。每天如果流程变了才改 |

`slug` 用小写英文和连字符，和内容对应，例如 `trump-waives-graham-act-sanctions`。有图时，文章图和首页图用同一个文件名。

## 首页要改哪里

欢迎页期次和署名在 `.w-sched`。页脚署名在 `footer > span.credit`。日期静态初值：

- `#w-date`：`2026年10月18日`（脚本仍会改成读者本地日期）
- `#dateline-date`：`2026年10月18日 星期日`

新闻只替换 `<!-- HERO -->` 到 `<!-- 市场 -->` 之前。下面这些 id 和 class 保留：

| 版块 | section id | 编号 |
|---|---|---|
| 国际 | `world` | 01 |
| 经济 | `econ` | 02 |
| 政治 | `poli` | 03 |
| 科技 | `tech` | 04 |
| AI 产业 | `ai` | 05 |
| 芯片 | `chips` | 06 |
| 美股 | `stocks` | 07 |
| Web3 | `crypto` | 08 |

头条结构：

```html
<div class="hero">
  <div class="hero-main">
    <span class="tag">头条 · TOP STORY</span>
    <figure class="ph ph-hero"><img src="img/YYYY-MM-DD/slug.webp" alt="..." loading="eager" onerror="this.closest('figure').remove()"></figure>
    <h2 class="serif"><a href="articles/YYYY-MM-DD/slug.html">标题</a></h2>
    <p class="dek">导语摘要</p>
    <div class="meta">来源 · YYYY-MM-DD · <a href="原文URL" target="_blank" rel="noopener">阅读原文 ↗</a></div>
  </div>
  <div class="hero-side">
    <div class="mini">
      <span class="tag">次条</span>
      <h3 class="serif"><a href="articles/YYYY-MM-DD/slug.html">标题</a></h3>
      <p>摘要</p>
      <div class="meta">来源 · YYYY-MM-DD</div>
    </div>
    <!-- 第二条次条同样结构 -->
  </div>
</div>
```

没有图时，整段 `figure` 删掉，不要留空 `img`。次条首页可以不放「原文」链接，原文放在文章页。

每个版块保持现有外壳，只换三张 `.card`：

```html
<section class="blk" id="world">
  <div class="sec-head"><span class="no">01</span><h2>国际</h2><span class="en">WORLD</span></div>
  <div class="grid">
    <div class="card">
      <span class="tag">短标签</span>
      <figure class="ph"><img src="img/YYYY-MM-DD/name.webp" alt="..." loading="lazy" onerror="this.closest('figure').remove()"></figure>
      <h3 class="serif"><a href="articles/YYYY-MM-DD/slug.html">标题</a></h3>
      <p>两三句摘要，数字和引语来自正文。</p>
      <div class="meta">来源 · MM-DD · <a href="原文URL" target="_blank" rel="noopener">原文 ↗</a></div>
    </div>
  </div>
</section>
```

首页标题用 `&quot;` 写引号。导航、市场折叠区 `#markets`、回到顶部按钮都不要动。

## 文章页

以现有文章页为模板，`<style>` 整段复制，不要新写样式。正文容器 `max-width: 700px`。

- `<html lang="zh-CN">`
- `<title>`：标题 + ` — 头版 · THE FRONT PAGE`
- 报头链接：`<a href="/?enter=1">头版 · THE FRONT PAGE</a>`
- kicker、返回链接按版块固定：

| 位置 | kicker | 返回 |
|---|---|---|
| 头条 | `头条 · FULL STORY` | `/?enter=1` |
| 次条 | `次条 · FULL STORY` | `/?enter=1` |
| 国际 | `国际 · FULL STORY` | `/?enter=1#world` |
| 经济 | `经济 · FULL STORY` | `/?enter=1#econ` |
| 政治 | `政治 · FULL STORY` | `/?enter=1#poli` |
| 科技 | `科技 · FULL STORY` | `/?enter=1#tech` |
| AI 产业 | `AI产业 · FULL STORY` | `/?enter=1#ai` |
| 芯片 | `芯片 · FULL STORY` | `/?enter=1#chips` |
| 美股 | `美股 · FULL STORY` | `/?enter=1#stocks` |
| Web3 | `Web3 · FULL STORY` | `/?enter=1#crypto` |

AI 产业的 kicker 是 `AI产业`，中间没有空格。

- byline：`来源 · YYYY-MM-DD · 头版编译`
- `<p class="lede">` 一段导语
- 有图时：`<figure class="ph"><img src="../../img/YYYY-MM-DD/name.webp" alt="..." loading="lazy" onerror="this.closest('figure').remove()"></figure>`
- `<article>` 里 5–9 个 `<p>`。导语不算在这 5–9 段里
- 文末：

```html
<div class="srcbox">原文来源：<a href="原文URL" target="_blank" rel="noopener">来源名 ↗</a><br>本页为头版基于原文的编译整理，关键事实与引文均来自原文；个别细节以原文为准。</div>
<div class="back"><a href="/?enter=1#world">← 返回头版</a></div>
<footer>© 2026 头版 · 内容来自公开网络来源，仅供参考</footer>
```

返回链的锚点按上表。文章页不要加 Grok Bot 署名，除非那一页原来就有采编署名。

## 配图

- 只使用原文页面上、可以合法随报道使用的图。拿不到、签名过期、或者画面上有出版方水印（例如卫报 CDN 把水印画进图里），就整张不用。
- 转成 WebP。最长边不超过 1200 像素，质量约 80。用 Pillow 即可：`image.save(path, "WEBP", quality=80)`。
- 站点 CSS 已经做了灰度、`object-fit: cover` 和 16:9。不要在文件上再做成灰度，也不要改 CSS。
- 首页路径是 `img/YYYY-MM-DD/...`。文章页路径是 `../../img/YYYY-MM-DD/...`。
- 八个版块的首页第一张卡片必须有本地 WebP 的 `figure`，标记与上面的卡片示例相同。只有确实找不到干净、无水印的图时才省略，并在当次出版记录里写明哪一版、为什么没有。其余卡片仍然可以没有图。

## 行情

浏览器里的取数顺序：先让两个大陆可达的源竞速，都失败再读对应的 JSON，JSON 也失败再用页内备用数组。加密货币仍是 Coinbase 与 OKX。常用市场和美股是东方财富与腾讯。时间标签用 `stamp()`，成功时写成 `实时 · 东财` 或 `实时 · 腾讯`。

新浪 `hq.sinajs.cn` 不用。它没有开放浏览器 CORS，而且非新浪 Referer 直接 403。script 标签也会带上本站 Referer，同样 403。第二源改用腾讯 `qt.gtimg.cn`：响应头 `Access-Control-Allow-Origin: *`，大陆可直连，普通 `fetch` 就能读。

| 品种 | 东财 `push2.eastmoney.com` 与 `push2delay.eastmoney.com` | 腾讯 `qt.gtimg.cn` |
|---|---|---|
| 黄金 XAU | `101.GC00Y`，COMEX 黄金。`f2` 现价，`f3` 涨跌幅 | `hf_GC`。逗号分隔，字段 0 是价，字段 1 是涨跌幅 |
| 白银 XAG | `101.SI00Y` | `hf_SI` |
| 布伦特 BRENT | `112.B00Y` | `hf_OIL`。腾讯这个代码是布伦特，不是 WTI |
| 美元/人民币 USDCNY | `133.USDCNH`，离岸美元兑人民币。这组接口没有在岸代码 | `whUSDCNY`，在岸。波浪号分隔，字段 3 是价，字段 13 是涨跌幅 |
| 美股十二只 | 纳斯达克 `105.SYMBOL`。台积电在纽交所，用 `106.TSM` | `usSYMBOL`。波浪号分隔，字段 3 是价，字段 32 是涨跌幅 |

东财两个主机放在同一条腿里用 `firstOk` 竞速，再和腾讯竞速。接口是 `/api/qt/ulist.np/get?fltt=2&invt=2&fields=f2,f3,f12&secids=...`。`fltt=2` 时价格是实际报价，`f3` 已经是百分数。超时沿用 `fetchT` 的 8 秒。

实时美股是 NVDA AAPL MSFT AVGO AMD TSM MU INTC META GOOGL AMZN ARM。SNDK 只留在 `US_FALLBACK`，不写入 `us-quotes.json`。不要把 Yahoo、Google 或 Coinbase 当成常用市场和美股的唯一路径。

三个 JSON 的形状不变：

```json
{
  "updated_utc": "2026-10-17T15:54:41Z",
  "updated_et": "美东 10-17 11:54",
  "quotes": [{ "symbol": "BTC", "price": 81205.79, "chg": -0.04 }]
}
```

`chg` 是百分数，涨为正、跌为负，保留两位小数。

| 文件 | symbol | 怎么取 |
|---|---|---|
| `crypto-quotes.json` | BTC ETH SOL XRP DOGE | Coinbase Exchange：`https://api.exchange.coinbase.com/products/{PAIR}/ticker` 的 `price`，同产品 `/stats` 的 `open`。`chg = (price - open) / open * 100`。交易对是 `BTC-USD`、`ETH-USD`、`SOL-USD`、`XRP-USD`、`DOGE-USD`。`updated_et` 写成取数时的美东时间 |
| `common-quotes.json` | XAU XAG BRENT USDCNY | 用上面的东财或腾讯快照。东财美元人民币是离岸 `USDCNH`，写入时 symbol 仍写 `USDCNY` |
| `us-quotes.json` | NVDA AAPL MSFT AVGO AMD TSM MU INTC META GOOGL AMZN ARM | 美东收盘，不是盘中。休市时沿用最近一个交易日的收盘。不要加入 SNDK |

浏览器不走 Yahoo。下面这段只是服务器侧的旧算法，Yahoo 在大陆经常打不开，刷新 JSON 时优先用上面的东财或腾讯。若仍用 Yahoo：v7 quote 接口会返回 401。用 v8，并带浏览器 User-Agent。`range=5d` 时的 `chartPreviousClose` 是好几天前的收盘，不能拿来算日涨跌。用最近两根非空日线收盘：

```python
import json, urllib.request
url = "https://query1.finance.yahoo.com/v8/finance/chart/GC=F?interval=1d&range=10d"
req = urllib.request.Request(url, headers={"User-Agent": "Mozilla/5.0"})
data = json.load(urllib.request.urlopen(req))
result = data["chart"]["result"][0]
closes = [c for c in result["indicators"]["quote"][0]["close"] if c is not None]
chg = (closes[-1] - closes[-2]) / closes[-2] * 100
```

对应代码：黄金 `GC=F` → XAU，白银 `SI=F` → XAG，布伦特 `BZ=F` → BRENT，美元兑人民币 `CNY=X` → USDCNY。外汇如果缺一根交易日线，用最近两根实际存在的收盘，并在 `updated_et` 里写明，例如 `美东 10-16 收盘 · 汇率 10-17`。

脚本里的备用数组跟这三份 JSON 用同一套数字：

- `FALLBACK` 对齐 `crypto-quotes.json`
- `CM_FALLBACK` 对齐 `common-quotes.json`
- `US_FALLBACK` 对齐 `us-quotes.json`，并保留文件里原有的 SNDK 一行。SNDK 不在 JSON 里。没有新的公开收盘就不要改 SNDK 的旧数字，也不要把它写进 JSON。备用标签保持「美东 MM-DD 收盘（备用）」这种已有句式，只改日期。

首页加密货币优先走浏览器里的 Coinbase / OKX。常用市场和美股优先走东财 / 腾讯。JSON 和页内备用数组只在实时源都失败时使用。

## 质量核对

出版前逐项看过：

- 文章页正好 27 个，首页 27 个链接都能打开对应文件。
- 头条 1 个、次条 2 个、八个版块各 3 张卡片。英雄位的三篇 slug 不出现在版块里。
- 每篇 `<article>` 内 5–9 段。有导语、有一条原文链接、`target="_blank"`、`rel="noopener"`，返回链接落在对应版块。
- 文中引语是中文。没有英文自注、没有「让我修正」、没有「原文没写」这类编辑口吻。
- 每张 `img` 的 src 都指向当天目录里真实存在的 `.webp`，文件头是 `RIFF....WEBP`。没有 `http` 图片地址。
- `index.html` 里 `AUTOMATED BY GROK BOT` 出现两次：欢迎页一次，页脚一次。没有 `AUTOMATED BY MUSE`，也没有「由 Muse 自动采编」。产品名 Muse Spark 之类留在新闻里。
- `#w-ed` 和 `#w-ed-en` 都是当期 `MM-DD`。
- `<style>` 与上一期相比没有差异。欢迎页去掉日期和署名文字后，结构与上一期相同。
- 三份 JSON 能被 `JSON.parse`，symbol 集合与上表一致，`chg` 是数字。
- 用本地静态服务器打开首页：欢迎页能进入正文，页脚署名是 Grok Bot，点开一条头条和一条版块稿，图片要么显示要么被 `onerror` 移除，返回链接回到对应位置。
