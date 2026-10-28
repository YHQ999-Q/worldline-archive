# Liora · 世界线档案

一个单页作品集网站。深蓝 + 紫色，曼陀罗主视觉，用「世界线 / 快穿档案」的方式把 6 个项目做成 6 个世界副本。网站署名统一使用 **Liora**。

- 纯 HTML + CSS + JavaScript，**不需要安装任何东西，也不需要构建**
- 图片、字体都用本地/系统自带，不依赖国外 CDN，国内打开也稳定
- 手机、平板、电脑自适应，手机端有底部导航
- 可以直接免费部署到 GitHub Pages

---

## 一、先在电脑上预览

打开这个文件夹，双击 `index.html`，用 Chrome 打开就能看。

如果图片不显示，检查 `index.html` 旁边是不是有一个 `assets` 文件夹，且里面的图片文件名没有改过。

---

## 二、上传到 GitHub（网页版，零基础版）

### 1. 建一个仓库

1. 打开 [github.com](https://github.com) 并登录（没有账号先注册）。
2. 点右上角 `+` → `New repository`。
3. 填写：
   - **Repository name**：`portfolio-website`（也可以叫别的，建议英文）
   - **Description**：可不填
   - 选择 **Public**（公开仓库才能免费开 Pages）
   - **不要**勾选 `Add a README file`（我们本地已经有 README）
4. 点 `Create repository`。

### 2. 上传文件

1. 在新仓库页面，点 `Add file` → `Upload files`。
2. 把本地 `portfolio-website` 文件夹里的这些东西一起拖进去：
   - `index.html`
   - `README.md`
   - `assets` **整个文件夹**（不要只拖里面的图片）
3. 等文件列表出现后，点绿色按钮 `Commit changes`。

> 上传完成后，仓库首页应该能直接看到 `index.html`、`README.md` 和 `assets` 文件夹。
> 如果只看到图片散在根目录，说明 `assets` 文件夹没被保留，请删掉重传。

> **不要上传 zip 压缩包。** GitHub Pages 不会自动解压，zip 只会被当成一个普通文件，网站打不开。请先在电脑上解压，再把里面的文件拖进去。
>
> 拖的时候要进入解压后的 `portfolio-website` 文件夹，选里面的 `index.html`、`README.md`、`assets` 一起拖；不要把最外层文件夹整个拖进去，否则会变成 `portfolio-website/index.html`，Pages 在根目录找不到首页。

### 3. 打开 GitHub Pages

1. 进入仓库的 `Settings`（设置）。
2. 左侧菜单找到 `Pages`。
3. `Build and deployment` → `Source` 选 **Deploy from a branch**。
4. `Branch` 选 `main`，文件夹选 `/ (root)`，点 `Save`。
5. 等 1–2 分钟，刷新这个页面，顶部会出现你的网址，形如：

```
https://你的GitHub用户名.github.io/portfolio-website/
```

6. 用电脑和手机各打开一次，确认图片、弹窗、底部导航都正常。

> 如果仓库名取成 `你的用户名.github.io`，网址会变成 `https://你的用户名.github.io/`。
> 第一次部署可能要等几分钟，也可以在仓库的 `Actions` 页看部署进度。

---

## 三、联系邮箱（如需更换）

页面里现在填的是 `1760600695@qq.com`。以后要换邮箱：

1. 用记事本、VS Code 或任意文本编辑器打开 `index.html`。
2. 按 `Ctrl + F` 搜索：`1760600695@qq.com`。
3. 会找到两处：

```html
<a class="btn btn-primary" id="email-link" href="mailto:1760600695@qq.com">发送任务简报 ...</a>
...
<span id="email-text">1760600695@qq.com</span>
```

4. 把两处 `1760600695@qq.com` 都换成新邮箱，`mailto:` 前缀保留。
   - 只改第一处的 `href` 也可以：页面显示会自动跟着变（脚本会读取 `href`）。
   - 但两处都改最稳妥。
5. 保存文件。如果已经上传过 GitHub，重新上传一次 `index.html` 即可。

> 想放微信二维码也可以：把二维码图片放进 `assets`，然后把「发送任务简报」按钮换成一个 `<img>` 标签。需要的话可以让 Claude 帮你改。

---

## 四、以后想改内容

### 改卡片文字 / 项目简介

`index.html` 里有两处项目文字：

1. **页面上看到的卡片**：搜索 `W—01`、`W—02`…… 在 `<div class="worlds-grid">` 里面。
2. **点开卡片后的详情弹窗**：在文件最下面的 `<script>` 里，搜索 `const WORLDS = [`。

每个项目在 `WORLDS` 数组里长这样：

```js
{
  coord: 'W—01',
  code: '智仪·天工',
  title: '天津大学大型仪器智能 Agent 平台',
  type: '高校科研 · ToB 产品',
  status: '已落地',
  cls: 'live',
  role: '项目主力负责人',
  summary: '……',
  media: 'assets/world-01-agent.png',
  meta: [ ... ],
  sections: [ ... ],
  tags: [ ... ]
}
```

**如果改了项目标题或简介，卡片和 `WORLDS` 两处都要改**，否则卡片上和弹窗里会不一致。

### 换图片

1. 把新图片放进 `assets` 文件夹。
2. 建议尺寸：横图，16:10 或 16:9，宽度 1200–1600px，文件小于 500KB。
3. 在 `index.html` 里搜索旧文件名，替换成新文件名；卡片里的 `<img src="...">` 和 `WORLDS` 里的 `media` 都要换。

> GitHub 区分大小写，`World-01.PNG` 和 `world-01.png` 不是同一个文件。

### 改颜色

`index.html` 顶部 `<style>` 里的 `:root` 就是配色表：

```css
--bg: #060918;          /* 深蓝背景 */
--violet: #a78bfa;      /* 主紫色 */
--indigo: #6d8bff;      /* 辅助蓝 */
--grad: linear-gradient(120deg, #7c9bff, #a78bfa, #d8b4fe);
```

改这几个值，整套页面的氛围会跟着变。建议保持深色背景 + 紫/蓝渐变。

### 改联系方式区的小字

搜索「下一段世界线」或「任务简报」，文案都在 `#contact` 这一节里。

---

## 五、文件结构

```
portfolio-website/
├─ index.html                 ← 整个网站（HTML + CSS + JS 都在里面）
├─ README.md                  ← 你现在看的说明书
└─ assets/
   ├─ world-01-agent.png      ← 天津大学平台截图
   ├─ world-02-lab.jpg        ← 兴趣迁移实验室截图
   ├─ world-03-library-card.jpg ← 上海图书馆数字人短片画面（卡片/弹窗用）
   ├─ world-03-library.jpg    ← 上海图书馆原始拼图（备用，页面暂未使用）
   └─ world-04-meituan.jpg    ← 美团 AIGC 作品
```

如果不需要备用图，可以删掉 `world-03-library.jpg`，不影响网页。

---

## 六、上线前检查清单

- [ ] 打开首页，标题是「穿过六个世界，把想法落成现实。」
- [ ] 6 张世界卡片都能点开，弹窗里有 4 段内容
- [ ] 筛选按钮「已落地 / 赛事 / 原型 / 商业」数量正确（3 / 3 / 1 / 2）
- [ ] 手机宽度 390px 左右打开，底部导航 4 个按钮都在，页面没有左右滑动
- [ ] 图片全部显示，没有裂图
- [ ] 邮箱已填写（`1760600695@qq.com`），点「发送任务简报」能打开邮件应用
- [ ] 点「复制邮箱」有「邮箱已复制」提示
- [ ] 商业保密项目只显示 NDA 和概述，没有放客户名/页面细节

---

## 七、常见问题

**Q：打开网址是 404？**  
A：先等 2–3 分钟；确认 `Settings → Pages` 里分支是 `main`、目录是 `/ (root)`；确认 `index.html` 在仓库最外层，不在子文件夹里。

**Q：图片全是裂的？**  
A：`assets` 文件夹没上传，或者文件名/大小写对不上。GitHub 上点开 `assets` 检查文件名。

**Q：页面没有样式，只有一堆文字？**  
A：`index.html` 没有放在仓库根目录，或者上传时文件被改了名。

**Q：手机上底部导航挡住了内容？**  
A：页脚已经预留了底部空间；如果你加了新内容，给页面最底部再加一点 `padding-bottom` 即可。

**Q：以后更新内容怎么办？**  
A：在 GitHub 仓库页面点 `Add file → Upload files`，把改过的文件重新拖进去，`Commit changes`。Pages 会自动重新部署，通常 1–2 分钟生效。

**Q：想绑定自己的域名？**  
A：先买域名，然后在 `Settings → Pages → Custom domain` 填写；再按 GitHub 提示去域名服务商加 CNAME 解析。新手可以先不折腾，`github.io` 网址已经够用。

---

## 八、说明

- 网站内容来自 `作品集.docx`，6 个项目、4 张配图；商业保密项目按原文只展示概述。
- 网站署名统一使用 **Liora**；编辑内容时不要把署名改回真实姓名。
- 「世界线 / 快穿」是视觉叙事，不是实际业务描述；项目事实以原文为准。
- 这是一个纯静态网站，没有后台、数据库和支付，所有交互都在浏览器本地完成。
